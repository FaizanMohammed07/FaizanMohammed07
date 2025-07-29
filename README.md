<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Faizan Ali | Full Stack Developer</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.12"></script>
  <script src="https://cdn.jsdelivr.net/npm/scrollreveal"></script>
  <style>
    body {
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: white;
      font-family: 'Fira Code', monospace;
    }
    .animate-fade {
      animation: fadeIn 1.2s ease-in-out forwards;
    }
    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(40px); }
      100% { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <main class="min-h-screen px-6 py-12">
    <section class="text-center animate-fade">
      <h1 class="text-4xl md:text-6xl font-bold mb-4">
        Hey, I'm <span class="text-indigo-400">Faizan Ali</span>
      </h1>
      <div class="text-xl md:text-2xl mt-2">
        <span id="typing"></span>
      </div>
    </section>

    <section class="mt-16 max-w-4xl mx-auto animate-fade">
      <h2 class="text-3xl font-bold mb-6 border-b border-gray-400 pb-2">About Me</h2>
      <ul class="list-disc list-inside leading-loose text-lg">
        <li>B.Tech IT Student at VJIT</li>
        <li>Building apps using MERN, EJS, Socket.io</li>
        <li>Exploring real-time systems, AI, WebSockets</li>
        <li>Founder of <strong>DevUp Society</strong> - mentoring and leading tech-driven growth</li>
        <li>Focus: Impactful, scalable, real-world tech solutions</li>
      </ul>
    </section>

    <section class="mt-16 max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12 animate-fade">
      <div>
        <h2 class="text-2xl font-semibold mb-4">Frontend Tech Stack</h2>
        <div class="grid grid-cols-2 gap-4 text-center">
          <span class="bg-gray-800 rounded-xl p-4">HTML5</span>
          <span class="bg-gray-800 rounded-xl p-4">CSS3</span>
          <span class="bg-gray-800 rounded-xl p-4">JavaScript</span>
          <span class="bg-gray-800 rounded-xl p-4">React.js</span>
          <span class="bg-gray-800 rounded-xl p-4">Bootstrap</span>
          <span class="bg-gray-800 rounded-xl p-4">Tailwind CSS</span>
          <span class="bg-gray-800 rounded-xl p-4">Material UI</span>
          <span class="bg-gray-800 rounded-xl p-4">EJS</span>
        </div>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-4">Backend & Tools</h2>
        <div class="grid grid-cols-2 gap-4 text-center">
          <span class="bg-gray-800 rounded-xl p-4">Node.js</span>
          <span class="bg-gray-800 rounded-xl p-4">Express.js</span>
          <span class="bg-gray-800 rounded-xl p-4">MongoDB</span>
          <span class="bg-gray-800 rounded-xl p-4">Socket.io</span>
          <span class="bg-gray-800 rounded-xl p-4">MVC Pattern</span>
          <span class="bg-gray-800 rounded-xl p-4">Postman</span>
          <span class="bg-gray-800 rounded-xl p-4">Git & GitHub</span>
          <span class="bg-gray-800 rounded-xl p-4">VS Code</span>
        </div>
      </div>
    </section>

    <section class="mt-16 text-center animate-fade">
      <h2 class="text-3xl font-semibold mb-4">Let’s Connect</h2>
      <p class="text-lg mb-4">Open to collaborations, internships, and speaking gigs</p>
      <div class="flex justify-center gap-6">
        <a href="https://linkedin.com/in/faizanmohammed07" class="hover:text-blue-400">LinkedIn</a>
        <a href="mailto:aliffaizan1212@gmail.com" class="hover:text-red-400">Gmail</a>
        <a href="https://github.com/FaizanMohammed07" class="hover:text-gray-300">GitHub</a>
      </div>
    </section>

    <footer class="mt-16 text-center text-sm text-gray-400">
      Made with ❤️ by Faizan Ali | DevUp Society
    </footer>
  </main>

  <script>
    new Typed("#typing", {
      strings: [
        "Full Stack Web Developer",
        "Founder of DevUp Society",
        "Real-time Application Builder",
        "Problem Solver | Mentor"
      ],
      typeSpeed: 40,
      backSpeed: 20,
      loop: true,
    });
    ScrollReveal().reveal('.animate-fade', { delay: 200, distance: '40px', duration: 1000, origin: 'bottom', reset: false });
  </script>
</body>
</html>
