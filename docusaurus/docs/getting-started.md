import React, { useState, useEffect } from 'react';
import { 
  Menu, X, Check, ArrowRight, BarChart, 
  Globe, ShoppingBag, Mail, Search, Share2, 
  Smartphone, MapPin, Phone, Star, ChevronRight,
  Facebook, Instagram, Linkedin, Twitter
} from 'lucide-react';

const RanialAgency = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [activeSection, setActiveSection] = useState('home');
  const [scrolled, setScrolled] = useState(false);

  // Handle scroll effect for navbar
  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const scrollToSection = (id) => {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
      setActiveSection(id);
      setIsMenuOpen(false);
    }
  };

  const services = [
    {
      title: "Social Media Marketing",
      icon: <Share2 className="w-8 h-8 text-blue-400" />,
      desc: "Strategic content and engagement strategies to grow your brand on all major platforms."
    },
    {
      title: "Facebook & Instagram Ads",
      icon: <Smartphone className="w-8 h-8 text-blue-400" />,
      desc: "High-converting ad campaigns targeting your ideal audience for maximum ROI."
    },
    {
      title: "SEO Optimization",
      icon: <Search className="w-8 h-8 text-blue-400" />,
      desc: "Rank higher on Google with our data-driven keyword research and on-page optimization."
    },
    {
      title: "Shopify Marketing",
      icon: <ShoppingBag className="w-8 h-8 text-blue-400" />,
      desc: "Boost your e-commerce sales with tailored strategies for Shopify stores."
    },
    {
      title: "Email Marketing",
      icon: <Mail className="w-8 h-8 text-blue-400" />,
      desc: "Automated flows and newsletters that turn leads into loyal recurring customers."
    },
    {
      title: "Website Optimization",
      icon: <Globe className="w-8 h-8 text-blue-400" />,
      desc: "Improving speed, UX/UI, and mobile responsiveness to lower bounce rates."
    }
  ];

  const portfolio = [
    {
      client: "E-Com Fashion Brand",
      category: "Facebook Ads",
      metric: "450% ROI",
      image: "https://images.unsplash.com/photo-1441986300917-64674bd600d8?auto=format&fit=crop&q=80&w=800",
      desc: "Scaled revenue from $5k to $25k/month in 90 days."
    },
    {
      client: "Tech Startup",
      category: "SEO & Content",
      metric: "+200% Traffic",
      image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&q=80&w=800",
      desc: "Dominated first-page keywords for competitive tech terms."
    },
    {
      client: "Local Service Biz",
      category: "Lead Gen",
      metric: "50+ Leads/Mo",
      image: "https://images.unsplash.com/photo-1556761175-5973dc0f32e7?auto=format&fit=crop&q=80&w=800",
      desc: "Revamped landing page and local SEO strategy."
    }
  ];

  const testimonials = [
    {
      name: "Chisom O.",
      role: "CEO, Glow Beauty",
      text: "Ranial Agency transformed our online presence. The team is professional, innovative, and results-driven. Highly recommended!"
    },
    {
      name: "David K.",
      role: "Founder, TechStart",
      text: "We saw a measurable increase in leads within the first month. Their communication and expertise are unmatched on Upwork."
    },
    {
      name: "Sarah J.",
      role: "Marketing Director",
      text: "Exceptional service! They handled our Shopify marketing seamlessly. The blue gradient branding matches their professional vibe perfectly."
    }
  ];

  const pricing = [
    {
      name: "Starter",
      price: "$500",
      period: "/month",
      features: ["Social Media Management", "5 Posts/Month", "Basic SEO Audit", "Monthly Report"],
      popular: false
    },
    {
      name: "Growth",
      price: "$1,200",
      period: "/month",
      features: ["Social Media & Ads", "15 Posts/Month", "Full SEO Package", "Bi-Weekly Meetings", "Email Automation"],
      popular: true
    },
    {
      name: "Enterprise",
      price: "Custom",
      period: "",
      features: ["Full Service Digital Marketing", "Dedicated Account Manager", "Unlimited Ad Spend Mgmt", "24/7 Support"],
      popular: false
    }
  ];

  return (
    <div className="font-sans text-slate-800 bg-slate-50 min-h-screen">
      
      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${scrolled ? 'bg-white shadow-md py-3' : 'bg-transparent py-5'}`}>
        <div className="container mx-auto px-6 flex justify-between items-center">
          <div className="flex items-center gap-2 cursor-pointer" onClick={() => scrollToSection('home')}>
            {/* Logo Placeholder / Icon mimicking the uploaded logo shape */}
            <div className="w-10 h-10 rounded bg-gradient-to-br from-blue-900 via-blue-700 to-blue-500 flex items-center justify-center text-white font-bold text-xl shadow-lg">
              R
            </div>
            <span className={`text-2xl font-bold tracking-tight ${scrolled ? 'text-blue-900' : 'text-white'}`}>
              RANIAL <span className="font-light">AGENCY</span>
            </span>
          </div>

          {/* Desktop Menu */}
          <div className="hidden md:flex items-center space-x-8">
            {['Home', 'Services', 'Portfolio', 'About', 'Pricing'].map((item) => (
              <button 
                key={item}
                onClick={() => scrollToSection(item.toLowerCase())}
                className={`font-medium hover:text-blue-500 transition-colors ${scrolled ? 'text-slate-700' : 'text-slate-100'}`}
              >
                {item}
              </button>
            ))}
            <button 
              onClick={() => scrollToSection('contact')}
              className="px-6 py-2.5 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-full transition-all shadow-lg hover:shadow-blue-500/30"
            >
              Contact Us
            </button>
          </div>

          {/* Mobile Menu Button */}
          <div className="md:hidden">
            <button 
              onClick={() => setIsMenuOpen(!isMenuOpen)}
              className={scrolled ? 'text-slate-800' : 'text-white'}
            >
              {isMenuOpen ? <X size={28} /> : <Menu size={28} />}
            </button>
          </div>
        </div>

        {/* Mobile Menu Dropdown */}
        {isMenuOpen && (
          <div className="md:hidden absolute top-full left-0 w-full bg-white shadow-xl py-4 flex flex-col items-center space-y-4 border-t border-slate-100">
            {['Home', 'Services', 'Portfolio', 'About', 'Pricing', 'Contact'].map((item) => (
              <button 
                key={item}
                onClick={() => scrollToSection(item.toLowerCase())}
                className="text-lg font-medium text-slate-700 hover:text-blue-600 w-full text-center py-2"
              >
                {item}
              </button>
            ))}
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <section id="home" className="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
        {/* Background Gradient */}
        <div className="absolute inset-0 bg-gradient-to-br from-blue-950 via-blue-800 to-blue-600 z-0"></div>
        <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/cubes.png')] opacity-10 z-0"></div>
        
        <div className="container mx-auto px-6 relative z-10 text-center lg:text-left flex flex-col lg:flex-row items-center gap-12">
          <div className="lg:w-1/2 text-white">
            <div className="inline-block px-4 py-1.5 rounded-full bg-blue-500/20 border border-blue-400/30 text-blue-100 text-sm font-medium mb-6 backdrop-blur-sm">
              🚀 Top-Rated on Upwork, Fiverr & Kwork
            </div>
            <h1 className="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight mb-6">
              Elevate Your Brand with <span className="text-transparent bg-clip-text bg-gradient-to-r from-blue-200 to-white">Digital Excellence</span>
            </h1>
            <p className="text-lg text-blue-100 mb-8 max-w-xl mx-auto lg:mx-0 leading-relaxed">
              We are Ranial Agency. We blend creativity with data-driven strategies to scale your business through SEO, social media, and precision advertising.
            </p>
            <div className="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start">
              <button onClick={() => scrollToSection('contact')} className="px-8 py-3.5 bg-white text-blue-900 font-bold rounded-full hover:bg-blue-50 transition-all shadow-xl hover:shadow-2xl transform hover:-translate-y-1">
                Get Started
              </button>
              <button onClick={() => scrollToSection('portfolio')} className="px-8 py-3.5 bg-transparent border-2 border-white/30 text-white font-semibold rounded-full hover:bg-white/10 transition-all flex items-center justify-center gap-2">
                View Work <ArrowRight size={18} />
              </button>
            </div>
            
            {/* Trusted By Badges */}
            <div className="mt-12 pt-8 border-t border-white/10 flex flex-wrap justify-center lg:justify-start gap-6 items-center opacity-80">
               <span className="text-sm font-light uppercase tracking-widest text-blue-200">Trusted on:</span>
               <div className="flex gap-4 font-bold text-lg">
                 <span className="flex items-center gap-1"><span className="w-2 h-2 rounded-full bg-green-500"></span> Fiverr</span>
                 <span className="flex items-center gap-1"><span className="w-2 h-2 rounded-full bg-green-400"></span> Upwork</span>
                 <span className="flex items-center gap-1"><span className="w-2 h-2 rounded-full bg-orange-500"></span> Kwork</span>
                 <span className="flex items-center gap-1"><span className="w-2 h-2 rounded-full bg-red-500"></span> Gmail</span>
               </div>
            </div>
          </div>
          
          <div className="lg:w-1/2 relative">
             <div className="relative z-10 rounded-2xl overflow-hidden shadow-2xl border-4 border-white/10 transform rotate-2 hover:rotate-0 transition-all duration-500">
                <img 
                  src="https://images.unsplash.com/photo-1531482615713-2afd69097998?auto=format&fit=crop&q=80&w=800" 
                  alt="Digital Marketing Team" 
                  className="w-full object-cover"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-blue-900/80 to-transparent flex items-end p-8">
                  <div className="text-white">
                    <p className="font-bold text-2xl">200% Growth</p>
                    <p className="text-sm opacity-80">Average client growth in 6 months</p>
                  </div>
                </div>
             </div>
             {/* Decorative Elements */}
             <div className="absolute -top-10 -right-10 w-32 h-32 bg-blue-500 rounded-full mix-blend-multiply filter blur-3xl opacity-50 animate-pulse"></div>
             <div className="absolute -bottom-10 -left-10 w-32 h-32 bg-purple-500 rounded-full mix-blend-multiply filter blur-3xl opacity-50 animate-pulse delay-700"></div>
          </div>
        </div>
      </section>

      {/* About Us Section */}
      <section id="about" className="py-20 bg-white">
        <div className="container mx-auto px-6">
          <div className="flex flex-col md:flex-row items-center gap-12">
            <div className="md:w-1/2">
               <div className="grid grid-cols-2 gap-4">
                 <img src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&q=80&w=400" className="rounded-2xl shadow-lg mt-8" alt="Team working" />
                 <img src="https://images.unsplash.com/photo-1551434678-e076c223a692?auto=format&fit=crop&q=80&w=400" className="rounded-2xl shadow-lg mb-8" alt="Strategy meeting" />
               </div>
            </div>
            <div className="md:w-1/2">
              <h2 className="text-blue-600 font-bold tracking-widest uppercase mb-2">Who We Are</h2>
              <h3 className="text-3xl md:text-4xl font-bold text-slate-900 mb-6">Innovative Solutions for Modern Brands</h3>
              <p className="text-slate-600 text-lg mb-6 leading-relaxed">
                Ranial Agency is a premier digital marketing firm based in Lagos, Nigeria. We specialize in helping businesses—from startups to established enterprises—navigate the complex digital landscape. 
              </p>
              <p className="text-slate-600 text-lg mb-8 leading-relaxed">
                Our mission is simple: to build trust and drive measurable results. Whether it's through compelling social media storytelling or technical SEO audits, we treat your business as our own.
              </p>
              <div className="grid grid-cols-2 gap-6">
                <div className="flex flex-col">
                  <span className="text-3xl font-bold text-blue-600">500+</span>
                  <span className="text-slate-500">Projects Completed</span>
                </div>
                <div className="flex flex-col">
                  <span className="text-3xl font-bold text-blue-600">98%</span>
                  <span className="text-slate-500">Client Satisfaction</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Services Section */}
      <section id="services" className="py-20 bg-slate-50">
        <div className="container mx-auto px-6">
          <div className="text-center mb-16">
            <h2 className="text-3xl md:text-4xl font-bold text-slate-900 mb-4">Our Expertise</h2>
            <p className="text-slate-600 max-w-2xl mx-auto">We offer a full suite of digital marketing services tailored to your specific goals and industry.</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {services.map((service, index) => (
              <div key={index} className="bg-white p-8 rounded-2xl shadow-sm hover:shadow-xl transition-shadow duration-300 border border-slate-100 group">
                <div className="w-14 h-14 bg-blue-50 rounded-xl flex items-center justify-center mb-6 group-hover:bg-blue-600 group-hover:text-white transition-colors duration-300">
                  <div className="group-hover:text-white transition-colors duration-300">
                     {React.cloneElement(service.icon, { className: "w-8 h-8 text-blue-600 group-hover:text-white" })}
                  </div>
                </div>
                <h3 className="text-xl font-bold text-slate-900 mb-3">{service.title}</h3>
                <p className="text-slate-600 leading-relaxed mb-4">{service.desc}</p>
                <a href="#contact" className="text-blue-600 font-semibold flex items-center gap-1 group-hover:gap-2 transition-all">
                  Learn more <ChevronRight size={16} />
                </a>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Portfolio Section */}
      <section id="portfolio" className="py-20 bg-white">
        <div className="container mx-auto px-6">
          <div className="flex flex-col md:flex-row justify-between items-end mb-12">
            <div>
              <h2 className="text-3xl md:text-4xl font-bold text-slate-900 mb-4">Featured Work</h2>
              <p className="text-slate-600">Real results we've achieved for our clients.</p>
            </div>
            <button className="hidden md:block text-blue-600 font-semibold hover:text-blue-800 transition-colors">View Full Portfolio &rarr;</button>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {portfolio.map((item, index) => (
              <div key={index} className="group relative overflow-hidden rounded-2xl shadow-lg cursor-pointer">
                <div className="absolute inset-0 bg-blue-900/80 opacity-0 group-hover:opacity-100 transition-opacity duration-300 z-10 flex flex-col justify-center items-center text-center p-6">
                  <h3 className="text-2xl font-bold text-white mb-2">{item.client}</h3>
                  <p className="text-blue-200 mb-4">{item.desc}</p>
                  <span className="px-4 py-2 bg-white text-blue-900 font-bold rounded-full">{item.metric}</span>
                </div>
                <img 
                  src={item.image} 
                  alt={item.client} 
                  className="w-full h-80 object-cover transform group-hover:scale-110 transition-transform duration-500"
                />
                <div className="absolute bottom-0 left-0 w-full p-6 bg-gradient-to-t from-black/80 to-transparent">
                  <p className="text-blue-300 text-sm font-medium mb-1">{item.category}</p>
                  <h3 className="text-white text-xl font-bold">{item.client}</h3>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Pricing Section */}
      <section id="pricing" className="py-20 bg-slate-50">
        <div className="container mx-auto px-6">
          <div className="text-center mb-16">
            <h2 className="text-3xl md:text-4xl font-bold text-slate-900 mb-4">Transparent Pricing</h2>
            <p className="text-slate-600 max-w-2xl mx-auto">Choose a package that fits your business needs. No hidden fees.</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
            {pricing.map((plan, index) => (
              <div key={index} className={`relative bg-white rounded-2xl p-8 shadow-lg border ${plan.popular ? 'border-blue-500 ring-2 ring-blue-500 ring-offset-2' : 'border-slate-100'}`}>
                {plan.popular && (
                  <div className="absolute top-0 right-0 bg-blue-600 text-white text-xs font-bold px-3 py-1 rounded-bl-lg rounded-tr-lg">
                    MOST POPULAR
                  </div>
                )}
                <h3 className="text-xl font-bold text-slate-900 mb-2">{plan.name}</h3>
                <div className="flex items-baseline mb-6">
                  <span className="text-4xl font-bold text-blue-600">{plan.price}</span>
                  <span className="text-slate-500 ml-1">{plan.period}</span>
                </div>
                <ul className="space-y-4 mb-8">
                  {plan.features.map((feature, i) => (
                    <li key={i} className="flex items-center text-slate-600">
                      <Check size={18} className="text-green-500 mr-2 flex-shrink-0" />
                      <span className="text-sm">{feature}</span>
                    </li>
                  ))}
                </ul>
                <button 
                  onClick={() => scrollToSection('contact')}
                  className={`w-full py-3 rounded-xl font-semibold transition-all ${plan.popular ? 'bg-blue-600 text-white hover:bg-blue-700 shadow-lg hover:shadow-blue-500/40' : 'bg-slate-100 text-slate-700 hover:bg-slate-200'}`}
                >
                  Choose {plan.name}
                </button>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Testimonials */}
      <section id="testimonials" className="py-20 bg-blue-900 text-white relative overflow-hidden">
        <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/stardust.png')] opacity-20"></div>
        <div className="container mx-auto px-6 relative z-10">
          <div className="text-center mb-12">
            <h2 className="text-3xl md:text-4xl font-bold mb-4">What Our Clients Say</h2>
          </div>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {testimonials.map((t, index) => (
              <div key={index} className="bg-blue-800/50 backdrop-blur-sm p-8 rounded-2xl border border-blue-700/50">
                <div className="flex gap-1 mb-4">
                  {[...Array(5)].map((_, i) => <Star key={i} size={16} className="text-yellow-400 fill-current" />)}
                </div>
                <p className="text-blue-100 italic mb-6">"{t.text}"</p>
                <div className="flex items-center gap-4">
                  <div className="w-10 h-10 rounded-full bg-blue-500 flex items-center justify-center font-bold text-white">
                    {t.name[0]}
                  </div>
                  <div>
                    <h4 className="font-bold">{t.name}</h4>
                    <p className="text-xs text-blue-300">{t.role}</p>
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Blog Teaser (Extra Feature) */}
      <section className="py-20 bg-white">
         <div className="container mx-auto px-6">
            <div className="flex justify-between items-center mb-10">
               <h2 className="text-3xl font-bold text-slate-900">Latest Marketing Insights</h2>
               <a href="#" className="text-blue-600 font-semibold hover:underline">View Blog</a>
            </div>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
               {[
                  { title: "5 Trends in Social Media for 2026", date: "Dec 12, 2025", cat: "Trends" },
                  { title: "Why SEO is Crucial for Local Business", date: "Nov 28, 2025", cat: "SEO" },
                  { title: "Maximizing ROI on Facebook Ads", date: "Nov 15, 2025", cat: "Advertising" }
               ].map((post, i) => (
                  <div key={i} className="border border-slate-100 rounded-xl p-6 hover:shadow-lg transition-all cursor-pointer">
                     <span className="text-xs font-bold text-blue-600 uppercase tracking-wider">{post.cat}</span>
                     <h3 className="text-xl font-bold mt-2 mb-3 text-slate-800">{post.title}</h3>
                     <p className="text-slate-500 text-sm">{post.date}</p>
                  </div>
               ))}
            </div>
         </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-20 bg-slate-50">
        <div className="container mx-auto px-6">
          <div className="bg-white rounded-3xl shadow-xl overflow-hidden flex flex-col lg:flex-row">
            {/* Contact Info */}
            <div className="lg:w-2/5 bg-gradient-to-br from-blue-900 to-blue-700 p-12 text-white flex flex-col justify-between">
              <div>
                <h2 className="text-3xl font-bold mb-6">Let's Discuss Your Project</h2>
                <p className="text-blue-100 mb-10">Ready to take your business to the next level? Fill out the form or reach us directly.</p>
                
                <div className="space-y-6">
                  <div className="flex items-start gap-4">
                    <div className="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center flex-shrink-0">
                      <Phone size={20} />
                    </div>
                    <div>
                      <p className="text-xs text-blue-300 uppercase font-bold tracking-wider">Phone</p>
                      <p className="text-lg">+234 812 982 5970</p>
                    </div>
                  </div>
                  
                  <div className="flex items-start gap-4">
                    <div className="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center flex-shrink-0">
                      <Mail size={20} />
                    </div>
                    <div>
                      <p className="text-xs text-blue-300 uppercase font-bold tracking-wider">Email</p>
                      <p className="text-lg">Info.ranialagency@gmail.com</p>
                    </div>
                  </div>
                  
                  <div className="flex items-start gap-4">
                    <div className="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center flex-shrink-0">
                      <MapPin size={20} />
                    </div>
                    <div>
                      <p className="text-xs text-blue-300 uppercase font-bold tracking-wider">Location</p>
                      <p className="text-lg">Lagos, Nigeria</p>
                    </div>
                  </div>
                </div>
              </div>

              <div className="mt-12">
                 <p className="text-sm text-blue-300 mb-4">Connect with us</p>
                 <div className="flex gap-4">
                    <div className="p-2 bg-white/10 rounded-full hover:bg-white/20 cursor-pointer transition-colors"><Facebook size={20} /></div>
                    <div className="p-2 bg-white/10 rounded-full hover:bg-white/20 cursor-pointer transition-colors"><Instagram size={20} /></div>
                    <div className="p-2 bg-white/10 rounded-full hover:bg-white/20 cursor-pointer transition-colors"><Linkedin size={20} /></div>
                    <div className="p-2 bg-white/10 rounded-full hover:bg-white/20 cursor-pointer transition-colors"><Twitter size={20} /></div>
                 </div>
              </div>
            </div>

            {/* Form */}
            <div className="lg:w-3/5 p-12">
              <form className="space-y-6">
                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div>
                    <label className="block text-sm font-medium text-slate-700 mb-2">First Name</label>
                    <input type="text" className="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all" placeholder="John" />
                  </div>
                  <div>
                    <label className="block text-sm font-medium text-slate-700 mb-2">Last Name</label>
                    <input type="text" className="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all" placeholder="Doe" />
                  </div>
                </div>
                
                <div>
                  <label className="block text-sm font-medium text-slate-700 mb-2">Email Address</label>
                  <input type="email" className="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all" placeholder="john@company.com" />
                </div>

                <div>
                  <label className="block text-sm font-medium text-slate-700 mb-2">Service Interested In</label>
                  <select className="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all">
                    <option>Social Media Marketing</option>
                    <option>SEO Optimization</option>
                    <option>Paid Advertising</option>
                    <option>Shopify Marketing</option>
                    <option>Other</option>
                  </select>
                </div>

                <div>
                  <label className="block text-sm font-medium text-slate-700 mb-2">Message</label>
                  <textarea rows="4" className="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all" placeholder="Tell us about your project goals..."></textarea>
                </div>

                <button type="button" className="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:-translate-y-1">
                  Send Message
                </button>
              </form>
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-slate-900 text-slate-400 py-12 border-t border-slate-800">
        <div className="container mx-auto px-6">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
            <div className="col-span-1 md:col-span-1">
               <div className="flex items-center gap-2 mb-6">
                  <div className="w-8 h-8 rounded bg-gradient-to-br from-blue-700 to-blue-500 flex items-center justify-center text-white font-bold text-lg">
                    R
                  </div>
                  <span className="text-xl font-bold text-white tracking-tight">
                    RANIAL <span className="font-light">AGENCY</span>
                  </span>
               </div>
               <p className="text-sm leading-relaxed mb-6">
                 Your trusted partner in digital growth. We build strategies that last and brands that inspire.
               </p>
            </div>
            
            <div>
              <h4 className="text-white font-bold mb-4">Quick Links</h4>
              <ul className="space-y-2 text-sm">
                <li><a href="#home" className="hover:text-blue-400 transition-colors">Home</a></li>
                <li><a href="#about" className="hover:text-blue-400 transition-colors">About Us</a></li>
                <li><a href="#services" className="hover:text-blue-400 transition-colors">Services</a></li>
                <li><a href="#portfolio" className="hover:text-blue-400 transition-colors">Portfolio</a></li>
                <li><a href="#contact" className="hover:text-blue-400 transition-colors">Contact</a></li>
              </ul>
            </div>

            <div>
              <h4 className="text-white font-bold mb-4">Services</h4>
              <ul className="space-y-2 text-sm">
                <li><a href="#" className="hover:text-blue-400 transition-colors">SEO Optimization</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Social Media Mgmt</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Facebook Ads</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Content Creation</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Web Development</a></li>
              </ul>
            </div>

            <div>
              <h4 className="text-white font-bold mb-4">Newsletter</h4>
              <p className="text-sm mb-4">Subscribe for the latest marketing tips.</p>
              <div className="flex">
                <input type="email" placeholder="Your email" className="bg-slate-800 text-white px-4 py-2 rounded-l-lg w-full focus:outline-none focus:ring-1 focus:ring-blue-500" />
                <button className="bg-blue-600 hover:bg-blue-500 px-4 py-2 rounded-r-lg text-white font-bold transition-colors">Go</button>
              </div>
            </div>
          </div>
          
          <div className="border-t border-slate-800 pt-8 flex flex-col md:flex-row justify-between items-center text-sm">
            <p>&copy; 2025 Ranial Agency. All rights reserved.</p>
            <div className="flex gap-6 mt-4 md:mt-0">
              <a href="#" className="hover:text-white transition-colors">Privacy Policy</a>
              <a href="#" className="hover:text-white transition-colors">Terms of Service</a>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default RanialAgency;
To create a new app, you may choose one of the following methods:

### npx

```sh
npx create-react-app@latest my-app
```

_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) comes with npm 5.2+ and higher, see [instructions for older npm versions](https://gist.github.com/gaearon/4064d3c23a77c74a3614c498a8bb1c5f))_

### npm

```sh
npm init react-app my-app
```

_`npm init <initializer>` is available in npm 6+_

### Yarn

```sh
yarn create react-app my-app
```

_`yarn create` is available in Yarn 0.25+_

### Selecting a template

You can now optionally start a new app from a template by appending `--template [template-name]` to the creation command.

If you don't select a template, we'll create your project with our base template.

Templates are always named in the format `cra-template-[template-name]`, however you only need to provide the `[template-name]` to the creation command.

```sh
npx create-react-app my-app --template [template-name]
```

> You can find a list of available templates by searching for ["cra-template-\*"](https://www.npmjs.com/search?q=cra-template-*) on npm.

Our [Custom Templates](custom-templates.md) documentation describes how you can build your own template.

#### Creating a TypeScript app

You can start a new TypeScript app using templates. To use our provided TypeScript template, append `--template typescript` to the creation command.

```sh
npx create-react-app my-app --template typescript
```

If you already have a project and would like to add TypeScript, see our [Adding TypeScript](adding-typescript.md) documentation.

### Selecting a package manager

When you create a new app, the CLI will use [npm](https://docs.npmjs.com) or [Yarn](https://yarnpkg.com/) to install dependencies, depending on which tool you use to run `create-react-app`. For example:

```sh
# Run this to use npm
npx create-react-app my-app
# Or run this to use yarn
yarn create react-app my-app
```

## Output

Running any of these commands will create a directory called `my-app` inside the current folder. Inside that directory, it will generate the initial project structure and install the transitive dependencies:

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

No configuration or complicated folder structures, only the files you need to build your app. Once the installation is done, you can open your project folder:

```sh
cd my-app
```

## Scripts

Inside the newly created project, you can run some built-in commands:

### `npm start` or `yarn start`

Runs the app in development mode. Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will automatically reload if you make changes to the code. You will see the build errors and lint warnings in the console.

<p align='center'>
<img src='https://cdn.jsdelivr.net/gh/marionebl/create-react-app@9f6282671c54f0874afd37a72f6689727b562498/screencast-error.svg' width='600' alt='Build errors' />
</p>

### `npm test` or `yarn test`

Runs the test watcher in an interactive mode. By default, runs tests related to files changed since the last commit.

[Read more about testing](running-tests.md).

### `npm run build` or `yarn build`

Builds the app for production to the `build` folder. It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.

Your app is ready to be deployed.
