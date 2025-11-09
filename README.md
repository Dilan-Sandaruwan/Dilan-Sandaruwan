import React, { useState, useEffect } from 'react';
import { Code, Database, Cloud, Palette, Mail, MessageSquare, Github, Linkedin, Twitter, Instagram, Award, Coffee, ChevronDown, Menu, X, ExternalLink } from 'lucide-react';

export default function Portfolio() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [activeSection, setActiveSection] = useState('home');
  const [isScrolled, setIsScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 50);
      
      const sections = ['home', 'about', 'skills', 'projects', 'contact'];
      const current = sections.find(section => {
        const element = document.getElementById(section);
        if (element) {
          const rect = element.getBoundingClientRect();
          return rect.top <= 150 && rect.bottom >= 150;
        }
        return false;
      });
      if (current) setActiveSection(current);
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const scrollToSection = (id) => {
    document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
    setIsMenuOpen(false);
  };

  const skills = {
    languages: ['C', 'Java', 'JavaScript', 'TypeScript', 'Python', 'PHP', 'Kotlin', 'Dart', 'C++', 'C#'],
    frontend: ['React', 'Next.js', 'Angular', 'TailwindCSS', 'Material UI', 'Bootstrap', 'Redux'],
    backend: ['Node.js', 'Express', 'Spring Boot', 'Hibernate', '.NET', 'GraphQL', 'NGINX'],
    database: ['PostgreSQL', 'MongoDB', 'MySQL', 'Redis', 'Firebase', 'SQLite'],
    cloud: ['Azure', 'Google Cloud', 'Firebase', 'Netlify', 'Heroku', 'Oracle'],
    tools: ['Docker', 'Kubernetes', 'Git', 'Jenkins', 'Postman', 'Selenium', 'Jest']
  };

  const projects = [
    {
      title: "Full-Stack Web Applications",
      description: "Scalable enterprise-level applications with modern architecture",
      tech: ["React", "Node.js", "PostgreSQL", "Docker"],
      gradient: "from-blue-500 to-cyan-500"
    },
    {
      title: "UI/UX Design Projects",
      description: "Modern, responsive interfaces with cutting-edge design patterns",
      tech: ["Figma", "TailwindCSS", "React", "TypeScript"],
      gradient: "from-purple-500 to-pink-500"
    },
    {
      title: "Database Architecture",
      description: "Optimized database systems with advanced querying capabilities",
      tech: ["PostgreSQL", "MongoDB", "Redis", "Spring Boot"],
      gradient: "from-green-500 to-emerald-500"
    },
    {
      title: "Cloud Solutions",
      description: "Scalable cloud-based applications with CI/CD pipelines",
      tech: ["Azure", "Docker", "Kubernetes", "Jenkins"],
      gradient: "from-orange-500 to-red-500"
    }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 text-white">
      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${isScrolled ? 'bg-slate-900/95 backdrop-blur-lg shadow-lg' : 'bg-transparent'}`}>
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            <div className="flex items-center space-x-2">
              <Code className="text-cyan-400" size={28} />
              <span className="text-xl font-bold bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
                Dilan Sandaruwan
              </span>
            </div>

            {/* Desktop Menu */}
            <div className="hidden md:flex space-x-8">
              {['home', 'about', 'skills', 'projects', 'contact'].map((item) => (
                <button
                  key={item}
                  onClick={() => scrollToSection(item)}
                  className={`capitalize transition-colors ${
                    activeSection === item ? 'text-cyan-400' : 'text-gray-300 hover:text-cyan-400'
                  }`}
                >
                  {item}
                </button>
              ))}
            </div>

            {/* Mobile Menu Button */}
            <button
              onClick={() => setIsMenuOpen(!isMenuOpen)}
              className="md:hidden text-white"
            >
              {isMenuOpen ? <X size={24} /> : <Menu size={24} />}
            </button>
          </div>
        </div>

        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="md:hidden bg-slate-900/95 backdrop-blur-lg">
            {['home', 'about', 'skills', 'projects', 'contact'].map((item) => (
              <button
                key={item}
                onClick={() => scrollToSection(item)}
                className="block w-full text-left px-4 py-3 capitalize hover:bg-slate-800 transition-colors"
              >
                {item}
              </button>
            ))}
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <section id="home" className="min-h-screen flex items-center justify-center relative overflow-hidden">
        <div className="absolute inset-0 bg-gradient-to-r from-cyan-500/10 to-purple-500/10 animate-pulse"></div>
        <div className="text-center z-10 px-4">
          <h1 className="text-5xl md:text-7xl font-bold mb-6 animate-fade-in">
            Hi, I'm <span className="bg-gradient-to-r from-cyan-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">
              Dilan Sandaruwan
            </span>
          </h1>
          <div className="text-2xl md:text-3xl text-gray-300 mb-8">
            <span className="inline-block animate-typing">Full Stack Developer</span>
            <span className="text-cyan-400 animate-pulse"> | </span>
            <span className="inline-block animate-typing-delay">UI/UX Enthusiast</span>
          </div>
          <p className="text-xl text-gray-400 mb-8 max-w-2xl mx-auto">
            Building scalable web applications with modern technologies from Kurunegala, Sri Lanka 🇱🇰
          </p>
          <div className="flex gap-4 justify-center mb-12">
            <button
              onClick={() => scrollToSection('projects')}
              className="px-8 py-3 bg-gradient-to-r from-cyan-500 to-purple-500 rounded-full font-semibold hover:scale-105 transform transition-all duration-300 shadow-lg hover:shadow-cyan-500/50"
            >
              View My Work
            </button>
            <button
              onClick={() => scrollToSection('contact')}
              className="px-8 py-3 border-2 border-cyan-400 rounded-full font-semibold hover:bg-cyan-400/10 transition-all duration-300"
            >
              Get In Touch
            </button>
          </div>
          <ChevronDown className="animate-bounce mx-auto text-cyan-400" size={32} />
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-20 px-4">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            About Me
          </h2>
          <div className="grid md:grid-cols-2 gap-8">
            <div className="bg-slate-800/50 backdrop-blur-lg rounded-2xl p-8 border border-slate-700 hover:border-cyan-500/50 transition-all duration-300 transform hover:scale-105">
              <Code className="text-cyan-400 mb-4" size={40} />
              <h3 className="text-2xl font-bold mb-4">Developer</h3>
              <p className="text-gray-400">
                Computer Science student with expertise in full-stack development. Passionate about creating elegant solutions to complex problems using modern technologies.
              </p>
            </div>
            <div className="bg-slate-800/50 backdrop-blur-lg rounded-2xl p-8 border border-slate-700 hover:border-purple-500/50 transition-all duration-300 transform hover:scale-105">
              <Palette className="text-purple-400 mb-4" size={40} />
              <h3 className="text-2xl font-bold mb-4">Designer</h3>
              <p className="text-gray-400">
                UI/UX enthusiast focused on creating beautiful, intuitive interfaces. Proficient in Figma, Photoshop, and modern design principles.
              </p>
            </div>
          </div>
          <div className="mt-8 bg-gradient-to-r from-slate-800/50 to-slate-700/50 backdrop-blur-lg rounded-2xl p-8 border border-slate-700">
            <h3 className="text-2xl font-bold mb-4 text-cyan-400">Current Focus</h3>
            <div className="grid md:grid-cols-2 gap-4">
              {[
                "Building scalable web applications",
                "Exploring modern UI/UX patterns",
                "Database optimization",
                "System architecture design",
                "Cloud technologies & DevOps",
                "Java OOP & Backend Architecture"
              ].map((focus, index) => (
                <div key={index} className="flex items-center space-x-2">
                  <span className="text-cyan-400">▹</span>
                  <span className="text-gray-300">{focus}</span>
                </div>
              ))}
            </div>
          </div>
        </div>
      </section>

      {/* Skills Section */}
      <section id="skills" className="py-20 px-4 bg-slate-900/50">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            Tech Arsenal
          </h2>
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            {Object.entries(skills).map(([category, items]) => (
              <div
                key={category}
                className="bg-slate-800/50 backdrop-blur-lg rounded-2xl p-6 border border-slate-700 hover:border-cyan-500/50 transition-all duration-300 transform hover:scale-105"
              >
                <h3 className="text-xl font-bold mb-4 capitalize text-cyan-400 flex items-center">
                  {category === 'languages' && <Code size={24} className="mr-2" />}
                  {category === 'frontend' && <Palette size={24} className="mr-2" />}
                  {category === 'backend' && <Database size={24} className="mr-2" />}
                  {category === 'database' && <Database size={24} className="mr-2" />}
                  {category === 'cloud' && <Cloud size={24} className="mr-2" />}
                  {category === 'tools' && <Award size={24} className="mr-2" />}
                  {category}
                </h3>
                <div className="flex flex-wrap gap-2">
                  {items.map((skill) => (
                    <span
                      key={skill}
                      className="px-3 py-1 bg-gradient-to-r from-cyan-500/10 to-purple-500/10 border border-cyan-500/30 rounded-full text-sm hover:scale-110 transition-transform duration-200"
                    >
                      {skill}
                    </span>
                  ))}
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Projects Section */}
      <section id="projects" className="py-20 px-4">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            Featured Projects
          </h2>
          <div className="grid md:grid-cols-2 gap-6">
            {projects.map((project, index) => (
              <div
                key={index}
                className="group relative bg-slate-800/50 backdrop-blur-lg rounded-2xl p-8 border border-slate-700 hover:border-transparent transition-all duration-300 overflow-hidden"
              >
                <div className={`absolute inset-0 bg-gradient-to-r ${project.gradient} opacity-0 group-hover:opacity-10 transition-opacity duration-300`}></div>
                <div className="relative z-10">
                  <h3 className="text-2xl font-bold mb-3">{project.title}</h3>
                  <p className="text-gray-400 mb-4">{project.description}</p>
                  <div className="flex flex-wrap gap-2 mb-4">
                    {project.tech.map((tech) => (
                      <span
                        key={tech}
                        className="px-3 py-1 bg-slate-700/50 rounded-full text-sm border border-slate-600"
                      >
                        {tech}
                      </span>
                    ))}
                  </div>
                  <button className="flex items-center space-x-2 text-cyan-400 hover:text-cyan-300 transition-colors">
                    <span>View Project</span>
                    <ExternalLink size={16} />
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-20 px-4 bg-slate-900/50">
        <div className="max-w-4xl mx-auto text-center">
          <h2 className="text-4xl font-bold mb-8 bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            Get In Touch
          </h2>
          <p className="text-xl text-gray-400 mb-12">
            Have a project in mind or want to collaborate? Let's connect!
          </p>
          <div className="grid md:grid-cols-2 gap-6 mb-12">
            <a
              href="mailto:dilansandaruwan0080@gmail.com"
              className="flex items-center justify-center space-x-3 bg-slate-800/50 backdrop-blur-lg rounded-2xl p-6 border border-slate-700 hover:border-cyan-500/50 transition-all duration-300 transform hover:scale-105"
            >
              <Mail className="text-cyan-400" size={24} />
              <div className="text-left">
                <div className="text-sm text-gray-400">Email</div>
                <div className="text-white">dilansandaruwan0080@gmail.com</div>
              </div>
            </a>
            <a
              href="https://t.me/+94774029980"
              target="_blank"
              rel="noopener noreferrer"
              className="flex items-center justify-center space-x-3 bg-slate-800/50 backdrop-blur-lg rounded-2xl p-6 border border-slate-700 hover:border-purple-500/50 transition-all duration-300 transform hover:scale-105"
            >
              <MessageSquare className="text-purple-400" size={24} />
              <div className="text-left">
                <div className="text-sm text-gray-400">Telegram</div>
                <div className="text-white">+94 77 402 9980</div>
              </div>
            </a>
          </div>
          <div className="flex justify-center space-x-6 mb-12">
            <a href="https://github.com/Dilan-Sandaruwan" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-cyan-400 transition-colors transform hover:scale-110">
              <Github size={32} />
            </a>
            <a href="https://linkedin.com" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-cyan-400 transition-colors transform hover:scale-110">
              <Linkedin size={32} />
            </a>
            <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-cyan-400 transition-colors transform hover:scale-110">
              <Twitter size={32} />
            </a>
            <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" className="text-gray-400 hover:text-cyan-400 transition-colors transform hover:scale-110">
              <Instagram size={32} />
            </a>
          </div>
          <a
            href="https://buymeacoffee.com/Dilan_Sandaruwan"
            target="_blank"
            rel="noopener noreferrer"
            className="inline-flex items-center space-x-2 px-8 py-3 bg-gradient-to-r from-yellow-500 to-orange-500 rounded-full font-semibold hover:scale-105 transform transition-all duration-300 shadow-lg hover:shadow-yellow-500/50"
          >
            <Coffee size={24} />
            <span>Buy Me a Coffee</span>
          </a>
        </div>
      </section>

      {/* Footer */}
      <footer className="py-8 text-center border-t border-slate-800">
        <p className="text-gray-400">
          "Code is poetry written in logic" - Dilan Sandaruwan
        </p>
        <p className="text-gray-500 mt-2">
          © 2025 Dilan Sandaruwan. Built with React & TailwindCSS
        </p>
      </footer>

      <style jsx>{`
        @keyframes fade-in {
          from {
            opacity: 0;
            transform: translateY(20px);
          }
          to {
            opacity: 1;
            transform: translateY(0);
          }
        }
        @keyframes typing {
          from {
            opacity: 0;
          }
          to {
            opacity: 1;
          }
        }
        .animate-fade-in {
          animation: fade-in 1s ease-out;
        }
        .animate-typing {
          animation: typing 2s ease-in-out;
        }
        .animate-typing-delay {
          animation: typing 2s ease-in-out 0.5s both;
        }
      `}</style>
    </div>
  );
}
