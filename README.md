import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence } from 'framer-motion';
import { useInView } from 'react-intersection-observer';
import {
  Briefcase,
  Layers,
  Cloud,
  Cpu,
  Database,
  TerminalSquare,
  BarChart2,
  Github,
  Linkedin,
  Mail,
  Twitter,
  Globe,
  Wrench,
  Code,
  Box,
  Server,
  Network,
  GitPullRequest,
  Slack,
  Sparkles,
} from 'lucide-react';

// Use this for the GitHub stats and contribution graph.
// Simply replace the `your-username` placeholder with your GitHub username.
const githubStatsUrl = "https://github-readme-stats.vercel.app/api?username=FaizanMohammed07&show_icons=true&theme=dracula&count_private=true&hide_border=true&include_all_commits=true";
const githubStreakUrl = "https://github-readme-streak-stats.herokuapp.com/?user=FaizanMohammed07&theme=dracula&hide_border=true&date_format=%5BY%5D%20M%20D";
const contributionGraphUrl = "https://github-contributions-api.joshuatz.dev/FaizanMohammed07?svg=true&dark=true&limit=52"; // An alternative for a more modern graph

// A professional, dark color palette for a sleek look
const colors = {
  background: '#1a202c', // Dark gray
  text: '#e2e8f0', // Light gray
  primary: '#63b3ed', // Blue
  secondary: '#4299e1', // Lighter blue
  card: '#2d3748', // Gray-blue
};

// --- Main App component for the README file ---
const App = () => {
  // Define your details here for easy customization
  const profile = {
    name: "Faizan Mohammed",
    titles: [
      "IT Undergraduate at VJIT",
      "LeadX D-Society",
      "MERN Stack Dev",
      "Cloud Architect (Azure | AWS)",
      "Innovating Solutions",
      "Leading the Build of Dev Platforms that Empower Skills"
    ],
    social: {
      github: "FaizanMohammed07",
      linkedin: "faizan-mohammed-developer",
      twitter: "your-twitter-handle", // Replace with your handle
      email: "your-email@example.com", // Replace with your email
      website: "your-website.com", // Replace with your website
    }
  };

  // Define skills with icons for a more visual appeal
  const skills = [
    {
      title: 'Frontend',
      icon: <Layers size={20} />,
      items: [
        { name: 'React.js', icon: <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg" className="w-4 h-4"><path d="M12 2.2c-.3 0-.6.1-.8.4l-9 15.6c-.3.5-.1 1.2.4 1.5.5.3 1.2.1 1.5-.4l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1c-.1 0-.3 0-.4.1L2.6 18.7c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.1-.7-.1zm0 2.4c-.2 0-.4.1-.5.3L2.6 19.3c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 3.8c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1.2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2z"></path><path d="M12 2.2c.2 0 .4.1.6.2l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 1c.1 0 .3 0 .4.1l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.1.6-.1zm0 2.4c.2 0 .4.1.5.3l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 3.8c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 1.2c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 2c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2z"></path><path d="M12.6 7.4c.4 0 .8.2 1 .5l8.1 14c.4.6.1 1.4-.5 1.7-.6.4-1.4.1-1.7-.5l-8-13.8c-.3-.5-.1-1.2.5-1.5.2-.1.5-.2.6-.2zm-1.2 0c.1 0 .3.1.4.2l8.1 14c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8-13.8c-.3-.5-.1-1.2.4-1.5.2-.1.5-.1.6-.1zm-1.2 0c.2 0 .4.1.5.3l8.1 14c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8-13.8c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm-1.2 0c.1 0 .3.1.4.2l8.1 14c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8-13.8c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2z"></path><circle cx="12" cy="12" r="3"></circle></svg> },
        { name: 'JavaScript (ES6+)', icon: <Code className="w-4 h-4" /> },
        { name: 'HTML5', icon: <Layers className="w-4 h-4" /> },
        { name: 'CSS3', icon: <Layers className="w-4 h-4" /> },
        { name: 'Tailwind CSS', icon: <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg" className="w-4 h-4"><path d="M12 2.2c-.3 0-.6.1-.8.4l-9 15.6c-.3.5-.1 1.2.4 1.5.5.3 1.2.1 1.5-.4l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1c-.1 0-.3 0-.4.1L2.6 18.7c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.1-.7-.1zm0 2.4c-.2 0-.4.1-.5.3L2.6 19.3c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 3.8c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1.2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2z"></path><path d="M12 2.2c.2 0 .4.1.6.2l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 1c.1 0 .3 0 .4.1l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.1.6-.1zm0 2.4c.2 0 .4.1.5.3l9 15.6c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.9-15.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 3.8c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 1.2c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2zm0 2c.1 0 .3.1.4.2l8.4 14.5c.3.5.1 1.2-.4 1.5-.5.3-1.2.1-1.5-.4l-8.4-14.5c-.3-.5-.1-1.2.4-1.5.2-.1.5-.2.6-.2z"></path></svg>},
        { name: 'Framer Motion', icon: <motion.div className="w-4 h-4"></motion.div> },
        { name: 'ShadCN/UI', icon: <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg" className="w-4 h-4"><path d="M12 2.2c-.3 0-.6.1-.8.4l-9 15.6c-.3.5-.1 1.2.4 1.5.5.3 1.2.1 1.5-.4l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1c-.1 0-.3 0-.4.1L2.6 18.7c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.1-.7-.1zm0 2.4c-.2 0-.4.1-.5.3L2.6 19.3c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.9-15.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 3.8c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 1.2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2zm0 2c-.1 0-.3.1-.4.2l-8.4 14.5c-.3.4-.1.8.3.9.4.2.8 0 .9-.3l8.4-14.5c.3-.5.1-1.2-.4-1.5-.2-.1-.5-.2-.6-.2z"></path></svg>},
        { name: 'React Router', icon: <GitPullRequest className="w-4 h-4" /> },
        { name: 'Vite', icon: <Sparkles className="w-4 h-4" /> },
        { name: 'Axios', icon: <Box className="w-4 h-4" /> },
        { name: 'Responsive Design', icon: <Layers className="w-4 h-4" /> },
        { name: 'Dark/Light Mode UI', icon: <Layers className="w-4 h-4" /> },
        { name: 'React Markdown', icon: <Layers className="w-4 h-4" /> },
      ]
    },
    {
      title: 'Backend',
      icon: <TerminalSquare size={20} />,
      items: [
        { name: 'Node.js', icon: <Server className="w-4 h-4" /> },
        { name: 'Express.js', icon: <Server className="w-4 h-4" /> },
        { name: 'REST APIs', icon: <Network className="w-4 h-4" /> },
        { name: 'JWT Authentication', icon: <Code className="w-4 h-4" /> },
        { name: 'Role-Based Access Control', icon: <Code className="w-4 h-4" /> },
        { name: 'bcryptjs', icon: <Code className="w-4 h-4" /> },
        { name: 'Multer', icon: <Code className="w-4 h-4" /> },
        { name: 'Nodemailer', icon: <Mail className="w-4 h-4" /> },
        { name: 'Cron Jobs', icon: <Code className="w-4 h-4" /> },
        { name: 'Puppeteer', icon: <Code className="w-4 h-4" /> },
        { name: 'html2pdf.js', icon: <Code className="w-4 h-4" /> },
      ]
    },
    {
      title: 'Database & Storage',
      icon: <Database size={20} />,
      items: [
        { name: 'MongoDB', icon: <Database className="w-4 h-4" /> },
        { name: 'SQL', icon: <Database className="w-4 h-4" /> },
        { name: 'MongoDB Atlas', icon: <Database className="w-4 h-4" /> },
        { name: 'Mongoose', icon: <Code className="w-4 h-4" /> },
        { name: 'Redis', icon: <Database className="w-4 h-4" /> },
        { name: 'Firebase Realtime Database', icon: <Database className="w-4 h-4" /> },
        { name: 'Firebase Storage', icon: <Database className="w-4 h-4" /> },
        { name: 'Cloudinary', icon: <Cloud className="w-4 h-4" /> },
      ]
    },
    {
      title: 'Real-Time Systems',
      icon: <Cpu size={20} />,
      items: [
        { name: 'Socket.io', icon: <Network className="w-4 h-4" /> },
        { name: 'WebSocket', icon: <Network className="w-4 h-4" /> },
        { name: 'Firebase Messaging', icon: <Mail className="w-4 h-4" /> },
        { name: 'Realtime Chat Systems', icon: <Slack className="w-4 h-4" /> },
        { name: 'Quiz Engine', icon: <Code className="w-4 h-4" /> },
        { name: 'Bug Reporting System', icon: <Code className="w-4 h-4" /> },
        { name: 'Live Collaboration Rooms', icon: <Code className="w-4 h-4" /> },
      ]
    },
    {
      title: 'AI & Integrations',
      icon: <Cloud size={20} />,
      items: [
        { name: 'OpenAI API', icon: <Cloud className="w-4 h-4" /> },
        { name: 'LangChain', icon: <Cloud className="w-4 h-4" /> },
        { name: 'AI Chatbot', icon: <Cloud className="w-4 h-4" /> },
        { name: 'Resume Analyzer', icon: <Cloud className="w-4 h-4" /> },
        { name: 'Roadmap Generator', icon: <Cloud className="w-4 h-4" /> },
        { name: 'Fuse.js', icon: <Cloud className="w-4 h-4" /> },
        { name: 'OneSignal', icon: <Cloud className="w-4 h-4" /> },
        { name: 'Google Calendar API', icon: <Cloud className="w-4 h-4" /> },
      ]
    },
    {
      title: 'DevOps & Deployment',
      icon: <Briefcase size={20} />,
      items: [
        { name: 'Git', icon: <Github className="w-4 h-4" /> },
        { name: 'GitHub', icon: <Github className="w-4 h-4" /> },
        { name: 'GitHub Actions', icon: <Code className="w-4 h-4" /> },
        { name: 'Vercel', icon: <Code className="w-4 h-4" /> },
        { name: 'Netlify', icon: <Code className="w-4 h-4" /> },
        { name: 'Render', icon: <Code className="w-4 h-4" /> },
        { name: 'Railway', icon: <Code className="w-4 h-4" /> },
        { name: 'DigitalOcean', icon: <Code className="w-4 h-4" /> },
        { name: 'Nginx', icon: <Code className="w-4 h-4" /> },
        { name: 'ESLint', icon: <Code className="w-4 h-4" /> },
        { name: 'Prettier', icon: <Code className="w-4 h-4" /> },
        { name: 'Husky', icon: <Code className="w-4 h-4" /> },
        { name: 'CI/CD Pipelines', icon: <Code className="w-4 h-4" /> },
      ]
    },
    {
      title: 'Analytics & Dashboards',
      icon: <BarChart2 size={20} />,
      items: [
        { name: 'Google Analytics', icon: <BarChart2 className="w-4 h-4" /> },
        { name: 'PostHog', icon: <BarChart2 className="w-4 h-4" /> },
        { name: 'Chart.js', icon: <BarChart2 className="w-4 h-4" /> },
        { name: 'Recharts', icon: <BarChart2 className="w-4 h-4" /> },
        { name: 'Admin Dashboards', icon: <BarChart2 className="w-4 h-4" /> },
      ]
    },
    {
      title: 'Utilities & Tools',
      icon: <Wrench size={20} />,
      items: [
        { name: 'Figma', icon: <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg" className="w-4 h-4"><path d="M5.5 24h-3a2.5 2.5 0 0 1-2.5-2.5v-3a2.5 2.5 0 0 1 2.5-2.5h3a2.5 2.5 0 0 1 2.5 2.5v3a2.5 2.5 0 0 1-2.5 2.5zM12 24h3a2.5 2.5 0 0 1 2.5-2.5v-3a2.5 2.5 0 0 1-2.5-2.5h-3a2.5 2.5 0 0 1-2.5 2.5v3a2.5 2.5 0 0 1 2.5 2.5zM19.5 17.5a2.5 2.5 0 0 1 2.5-2.5h3a2.5 2.5 0 0 1 2.5 2.5v3a2.5 2.5 0 0 1-2.5 2.5h-3a2.5 2.5 0 0 1-2.5-2.5v-3zM5.5 17.5h-3a2.5 2.5 0 0 1-2.5-2.5v-3a2.5 2.5 0 0 1 2.5-2.5h3a2.5 2.5 0 0 1 2.5 2.5v3a2.5 2.5 0 0 1-2.5 2.5zM12 17.5h3a2.5 2.5 0 0 1 2.5-2.5v-3a2.5 2.5 0 0 1-2.5-2.5h-3a2.5 2.5 0 0 1-2.5 2.5v3a2.5 2.5 0 0 1 2.5 2.5zM12 5.5h-3a2.5 2.5 0 0 1-2.5-2.5v-3a2.5 2.5 0 0 1 2.5-2.5h3a2.5 2.5 0 0 1 2.5 2.5v3a2.5 2.5 0 0 1-2.5 2.5z"></path></svg>},
        { name: 'Trello', icon: <Code className="w-4 h-4" /> },
        { name: 'Notion', icon: <Code className="w-4 h-4" /> },
        { name: 'Markdown Rendering', icon: <Code className="w-4 h-4" /> },
        { name: 'File Uploads', icon: <Code className="w-4 h-4" /> },
        { name: 'Search System', icon: <Code className="w-4 h-4" /> },
        { name: 'Resource Library', icon: <Code className="w-4 h-4" /> },
        { name: 'Internship Matcher', icon: <Code className="w-4 h-4" /> },
        { name: 'Certificate Vault', icon: <Code className="w-4 h-4" /> },
        { name: 'Learning Calendar', icon: <Code className="w-4 h-4" /> },
        { name: 'Project Collaboration Tools', icon: <Code className="w-4 h-4" /> },
        { name: 'Gamification System', icon: <Code className="w-4 h-4" /> },
        { name: 'Community Forum', icon: <Code className="w-4 h-4" /> },
      ]
    }
  ];

  // State to manage the title animation
  const [currentTitleIndex, setCurrentTitleIndex] = useState(0);

  // Effect to cycle through the titles every few seconds
  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentTitleIndex((prevIndex) => (prevIndex + 1) % profile.titles.length);
    }, 4000); // Change title every 4 seconds
    return () => clearInterval(interval);
  }, [profile.titles.length]);

  return (
    <div className="bg-gray-900 text-gray-200 min-h-screen p-8 font-sans">
      <div className="max-w-6xl mx-auto space-y-12">
        {/* Animated Header Section */}
        <div className="flex flex-col items-center justify-center text-center space-y-6 pt-16">
          <motion.h1
            initial={{ opacity: 0, y: -50 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 1 }}
            className="text-5xl md:text-7xl font-bold tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-indigo-600"
          >
            {profile.name}
          </motion.h1>
          <motion.p
            initial={{ opacity: 0, scale: 0.8 }}
            animate={{ opacity: 1, scale: 1 }}
            transition={{ duration: 0.8, delay: 0.5 }}
            className="text-lg md:text-2xl text-gray-400 tracking-wide font-light"
          >
            <AnimatePresence mode="wait">
              <motion.span
                key={currentTitleIndex}
                initial={{ y: 20, opacity: 0 }}
                animate={{ y: 0, opacity: 1 }}
                exit={{ y: -20, opacity: 0 }}
                transition={{ duration: 0.5 }}
              >
                {profile.titles[currentTitleIndex]}
              </motion.span>
            </AnimatePresence>
          </motion.p>
        </div>

        {/* Social Links Section */}
        <div className="flex justify-center space-x-6 text-gray-400 text-3xl">
          {profile.social.github && (
            <motion.a
              href={`https://github.com/${profile.social.github}`}
              target="_blank"
              rel="noopener noreferrer"
              whileHover={{ scale: 1.2, color: colors.primary }}
              transition={{ type: "spring", stiffness: 400 }}
              aria-label="GitHub Profile"
            >
              <Github />
            </motion.a>
          )}
          {profile.social.linkedin && (
            <motion.a
              href={`https://linkedin.com/in/${profile.social.linkedin}`}
              target="_blank"
              rel="noopener noreferrer"
              whileHover={{ scale: 1.2, color: colors.primary }}
              transition={{ type: "spring", stiffness: 400 }}
              aria-label="LinkedIn Profile"
            >
              <Linkedin />
            </motion.a>
          )}
          {profile.social.twitter && (
            <motion.a
              href={`https://twitter.com/${profile.social.twitter}`}
              target="_blank"
              rel="noopener noreferrer"
              whileHover={{ scale: 1.2, color: colors.primary }}
              transition={{ type: "spring", stiffness: 400 }}
              aria-label="Twitter Profile"
            >
              <Twitter />
            </motion.a>
          )}
          {profile.social.email && (
            <motion.a
              href={`mailto:${profile.social.email}`}
              whileHover={{ scale: 1.2, color: colors.primary }}
              transition={{ type: "spring", stiffness: 400 }}
              aria-label="Email Me"
            >
              <Mail />
            </motion.a>
          )}
          {profile.social.website && (
            <motion.a
              href={`https://${profile.social.website}`}
              target="_blank"
              rel="noopener noreferrer"
              whileHover={{ scale: 1.2, color: colors.primary }}
              transition={{ type: "spring", stiffness: 400 }}
              aria-label="Personal Website"
            >
              <Globe />
            </motion.a>
          )}
        </div>

        {/* Skills Section */}
        <div className="space-y-8">
          {skills.map((category, index) => (
            <SkillCategory key={index} category={category} />
          ))}
        </div>

        {/* GitHub Stats Section */}
        <div className="space-y-4 pt-8">
          <h2 className="text-3xl font-semibold text-center text-blue-400">My GitHub Stats</h2>
          <div className="flex flex-col md:flex-row justify-center items-center gap-4">
            <img src={githubStatsUrl} alt="GitHub Stats" className="rounded-lg shadow-xl" />
            <img src={githubStreakUrl} alt="GitHub Streak" className="rounded-lg shadow-xl" />
          </div>
          <div className="flex justify-center mt-8">
            {/* The contribution graph might be slow to load, but it's a great visual */}
            <img src={contributionGraphUrl} alt="GitHub Contribution Graph" className="w-full max-w-2xl rounded-lg shadow-xl" />
          </div>
        </div>
      </div>
    </div>
  );
};

// SkillCategory component for individual skill groups
const SkillCategory = ({ category }) => {
  // Use a ref and intersection observer to trigger animation when the component is in view
  const { ref, inView } = useInView({
    triggerOnce: true, // Only animate once
    threshold: 0.1, // Trigger when 10% of the component is visible
  });

  const categoryVariants = {
    hidden: { opacity: 0, y: 50 },
    visible: {
      opacity: 1,
      y: 0,
      transition: {
        duration: 0.6,
        ease: "easeOut",
        staggerChildren: 0.05, // Stagger the animation of children items
      },
    },
  };

  const itemVariants = {
    hidden: { opacity: 0, y: 20 },
    visible: { opacity: 1, y: 0 },
  };

  return (
    <motion.div
      ref={ref}
      variants={categoryVariants}
      initial="hidden"
      animate={inView ? "visible" : "hidden"}
      className="p-6 bg-gray-800 rounded-xl shadow-xl border border-gray-700"
    >
      <div className="flex items-center space-x-3 mb-4">
        {category.icon}
        <h3 className="text-xl font-semibold text-blue-400">{category.title}</h3>
      </div>
      <motion.ul className="flex flex-wrap gap-3">
        {category.items.map((item, index) => (
          <motion.li
            key={index}
            variants={itemVariants}
            whileHover={{ scale: 1.1, backgroundColor: '#3b82f6' }} // Pop on hover
            transition={{ type: "spring", stiffness: 400, damping: 10 }}
            className="flex items-center space-x-2 px-4 py-2 bg-gray-700 text-gray-300 rounded-full text-sm font-medium transition-colors duration-200 cursor-pointer"
          >
            {item.icon}
            <span>{item.name}</span>
          </motion.li>
        ))}
      </motion.ul>
    </motion.div>
  );
};

export default App;
