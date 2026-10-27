import React, { useState, useEffect } from 'react';
import { 
  Menu, X, ChevronRight, ArrowUp, Mail, User, Briefcase, 
  Phone, Instagram, Music, Camera, Cpu, Wrench, Film, Award, 
  Heart, CheckCircle2, Send, MessageCircle, Video
} from 'lucide-react';

export default function App() {
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
  const [activeSection, setActiveSection] = useState('home');
  const [formData, setFormData] = useState({ email: '', name: '', message: '' });
  const [submitted, setSubmitted] = useState(false);

  // Handle scroll spy for navigation
  useEffect(() => {
    const handleScroll = () => {
      const sections = ['home', 'bio', 'timeline', 'contact'];
      const scrollPosition = window.scrollY + 200;

      for (const section of sections) {
        const el = document.getElementById(section);
        if (el) {
          const top = el.offsetTop;
          const height = el.offsetHeight;
          if (scrollPosition >= top && scrollPosition < top + height) {
            setActiveSection(section);
            break;
          }
        }
      }
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const scrollToSection = (id) => {
    setMobileMenuOpen(false);
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!formData.email || !formData.name || !formData.message) return;
    setSubmitted(true);
    setTimeout(() => {
      setSubmitted(false);
      setFormData({ email: '', name: '', message: '' });
    }, 4000);
  };

  return (
    <div className="min-h-screen bg-[#0d0d0d] text-[#e5e5e5] font-sans selection:bg-[#ff7a00] selection:text-white antialiased overflow-x-hidden">
      
      {/* HEADER / NAVIGATION */}
      <header className="fixed top-0 left-0 right-0 z-50 bg-[#0d0d0d]/80 backdrop-blur-md border-b border-white/5">
        <div className="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
          {/* Logo / Name */}
          <div 
            onClick={() => scrollToSection('home')}
            className="cursor-pointer flex items-center gap-2 group"
          >
            <span className="text-xl md:text-2xl font-bold tracking-tight text-white group-hover:text-[#ff7a00] transition-colors font-serif">
              ARSYA ZAIN NURRAFIF<span className="text-[#ff7a00]">.</span>
            </span>
          </div>

          {/* Desktop Navigation */}
          <nav className="hidden md:flex items-center gap-8 text-sm font-medium tracking-wide">
            <button 
              onClick={() => scrollToSection('home')}
              className={`transition-colors hover:text-[#ff7a00] ${activeSection === 'home' ? 'text-[#ff7a00]' : 'text-zinc-400'}`}
            >
              Home
            </button>
            <button 
              onClick={() => scrollToSection('bio')}
              className={`transition-colors hover:text-[#ff7a00] ${activeSection === 'bio' ? 'text-[#ff7a00]' : 'text-zinc-400'}`}
            >
              Bio
            </button>
            <button 
              onClick={() => scrollToSection('timeline')}
              className={`transition-colors hover:text-[#ff7a00] ${activeSection === 'timeline' ? 'text-[#ff7a00]' : 'text-zinc-400'}`}
            >
              Timeline
            </button>
            <button 
              onClick={() => scrollToSection('contact')}
              className={`transition-colors hover:text-[#ff7a00] ${activeSection === 'contact' ? 'text-[#ff7a00]' : 'text-zinc-400'}`}
            >
              Contact
            </button>
          </nav>

          {/* Social Quick Links Bar in Header */}
          <div className="hidden lg:flex items-center gap-3">
            <a 
              href="https://www.instagram.com/arsya.rafif?psln=MWh1bjhlMnU0MTViOQ==" 
              target="_blank" 
              rel="noreferrer"
              className="p-2 rounded-full bg-white/5 border border-white/10 text-zinc-300 hover:text-[#ff7a00] hover:border-[#ff7a00]/50 transition-all text-xs flex items-center gap-1.5 px-3"
            >
              <Instagram size={14} /> IG
            </a>
            <a 
              href="https://www.tiktok.com/@arsya_zannrrff?_r=1&_t=ZS-9AuEGpKOGqS" 
              target="_blank" 
              rel="noreferrer"
              className="p-2 rounded-full bg-white/5 border border-white/10 text-zinc-300 hover:text-[#ff7a00] hover:border-[#ff7a00]/50 transition-all text-xs flex items-center gap-1.5 px-3"
            >
              <Video size={14} /> TikTok
            </a>
            <a 
              href="https://wa.me/qr/ADU7H25XOS33E1" 
              target="_blank" 
              rel="noreferrer"
              className="p-2 rounded-full bg-[#25D366]/20 border border-[#25D366]/40 text-[#25D366] hover:bg-[#25D366]/30 transition-all text-xs flex items-center gap-1.5 px-3 font-medium"
            >
              <MessageCircle size={14} /> WhatsApp
            </a>
          </div>

          {/* Mobile Menu Button */}
          <button 
            onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
            className="md:hidden text-white p-2 focus:outline-none"
            aria-label="Toggle Menu"
          >
            {mobileMenuOpen ? <X size={24} /> : <Menu size={24} />}
          </button>
        </div>

        {/* Mobile Dropdown */}
        {mobileMenuOpen && (
          <div className="md:hidden absolute top-20 left-0 right-0 bg-[#121212] border-b border-white/10 px-6 py-6 flex flex-col gap-4 shadow-2xl">
            <button 
              onClick={() => scrollToSection('home')}
              className="text-left py-2 text-lg font-medium text-zinc-300 hover:text-[#ff7a00]"
            >
              Home
            </button>
            <button 
              onClick={() => scrollToSection('bio')}
              className="text-left py-2 text-lg font-medium text-zinc-300 hover:text-[#ff7a00]"
            >
              Bio
            </button>
            <button 
              onClick={() => scrollToSection('timeline')}
              className="text-left py-2 text-lg font-medium text-zinc-300 hover:text-[#ff7a00]"
            >
              Timeline
            </button>
            <button 
              onClick={() => scrollToSection('contact')}
              className="text-left py-2 text-lg font-medium text-zinc-300 hover:text-[#ff7a00]"
            >
              Contact
            </button>
            <div className="pt-4 border-t border-white/10 flex flex-wrap gap-2">
              <a href="https://www.instagram.com/arsya.rafif?psln=MWh1bjhlMnU0MTViOQ==" target="_blank" rel="noreferrer" className="px-3 py-2 rounded-lg bg-zinc-800 text-xs text-white flex items-center gap-1.5">
                <Instagram size={14} /> Instagram
              </a>
              <a href="https://www.tiktok.com/@arsya_zannrrff?_r=1&_t=ZS-9AuEGpKOGqS" target="_blank" rel="noreferrer" className="px-3 py-2 rounded-lg bg-zinc-800 text-xs text-white flex items-center gap-1.5">
                <Video size={14} /> TikTok
              </a>
              <a href="https://wa.me/qr/ADU7H25XOS33E1" target="_blank" rel="noreferrer" className="px-3 py-2 rounded-lg bg-[#25D366]/20 text-[#25D366] text-xs flex items-center gap-1.5 font-medium">
                <MessageCircle size={14} /> WhatsApp
              </a>
            </div>
          </div>
        )}
      </header>

      {/* HERO SECTION */}
      <section id="home" className="relative pt-28 md:pt-36 pb-16 md:pb-24 overflow-hidden border-b border-white/5">
        <div className="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
          
          {/* Left Text Column */}
          <div className="lg:col-span-6 z-10">
            <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/5 border border-white/10 text-[#ff7a00] text-xs font-semibold uppercase tracking-widest mb-6">
              PELAJAR & CREATIVE TALENT MAN PACITAN
            </div>
            <h1 className="text-5xl md:text-7xl font-extrabold tracking-tight text-white mb-6 leading-[1.1] font-serif">
              Arsya <br className="hidden sm:block" />
              Zain<span className="text-[#ff7a00]">.</span>
            </h1>
            <p className="text-lg md:text-xl text-zinc-400 max-w-lg mb-10 leading-relaxed">
              Mengenal lebih dekat sosok pemuda asal Pacitan, pelajar MAN Pacitan yang berdedikasi dalam seni musik, teknologi jaringan, fotografi, dan media kreatif.
            </p>
            <div className="flex flex-wrap items-center gap-4">
              <button 
                onClick={() => scrollToSection('bio')}
                className="px-8 py-4 rounded-full bg-[#ff7a00] hover:bg-[#e06c00] text-white font-semibold transition-all duration-300 shadow-lg shadow-[#ff7a00]/20 flex items-center gap-2"
              >
                Jelajahi Biografi <ChevronRight size={18} />
              </button>
              <button 
                onClick={() => scrollToSection('contact')}
                className="px-8 py-4 rounded-full bg-white/5 hover:bg-white/10 text-white font-semibold border border-white/10 transition-all duration-300"
              >
                Hubungi Saya
              </button>
            </div>
          </div>

          {/* Right Image / Hero Visual Column */}
          <div className="lg:col-span-6 relative">
            <div className="relative mx-auto max-w-md lg:max-w-none rounded-3xl overflow-hidden border border-white/10 bg-zinc-900 shadow-2xl group">
              <div className="absolute inset-0 bg-gradient-to-t from-[#0d0d0d] via-transparent to-transparent opacity-80 z-10"></div>
              {/* Featured Hero Portrait */}
              <div className="h-[420px] md:h-[520px] w-full relative overflow-hidden bg-zinc-950">
                <img 
                  src="IMG_4816.jpg" 
                  alt="Arsya Zain Nurrafif" 
                  className="w-full h-full object-cover object-center group-hover:scale-105 transition-transform duration-700"
                />
                <div className="absolute bottom-0 inset-x-0 p-6 z-20 bg-gradient-to-t from-black/90 via-black/50 to-transparent">
                  <h3 className="text-2xl font-bold text-white mb-1">Arsya Zain Nurrafif</h3>
                  <p className="text-[#ff7a00] text-sm font-medium">"Menjadi lebih baik dari sebelumnya"</p>
                </div>
              </div>
            </div>

            {/* Floating Social Icons */}
            <div className="absolute right-4 bottom-8 lg:right-[-20px] lg:bottom-12 z-30 flex flex-col gap-3">
              <a href="https://www.instagram.com/arsya.rafif?psln=MWh1bjhlMnU0MTViOQ==" target="_blank" rel="noreferrer" className="w-10 h-10 rounded-full bg-zinc-900/90 border border-white/10 flex items-center justify-center text-zinc-300 hover:text-[#ff7a00] hover:border-[#ff7a00]/50 transition-all shadow-lg" title="Instagram">
                <Instagram size={18} />
              </a>
              <a href="https://www.tiktok.com/@arsya_zannrrff?_r=1&_t=ZS-9AuEGpKOGqS" target="_blank" rel="noreferrer" className="w-10 h-10 rounded-full bg-zinc-900/90 border border-white/10 flex items-center justify-center text-zinc-300 hover:text-[#ff7a00] hover:border-[#ff7a00]/50 transition-all shadow-lg" title="TikTok">
                <Video size={18} />
              </a>
              <a href="https://wa.me/qr/ADU7H25XOS33E1" target="_blank" rel="noreferrer" className="w-10 h-10 rounded-full bg-[#25D366]/20 border border-[#25D366]/40 flex items-center justify-center text-[#25D366] hover:bg-[#25D366]/30 transition-all shadow-lg" title="WhatsApp">
                <MessageCircle size={18} />
              </a>
            </div>
          </div>

        </div>
      </section>

      {/* BIO SECTION / Latar Belakang & Keluarga */}
      <section id="bio" className="py-24 bg-[#0d0d0d] border-b border-white/5 relative">
        <div className="max-w-7xl mx-auto px-6">
          
          <div className="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center mb-20">
            <div className="lg:col-span-5">
              <div className="rounded-2xl overflow-hidden border border-white/10 bg-zinc-900/50 p-2 shadow-xl group">
                <div className="h-[400px] rounded-xl overflow-hidden relative">
                  <img 
                    src="IMG-20261027-WA0110.jpg" 
                    alt="Arsya behind the camera" 
                    className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                  />
                  <div className="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                  <div className="absolute bottom-6 left-6 right-6 z-10">
                    <span className="text-[#ff7a00] text-xs font-semibold tracking-wider uppercase mb-1 block">PROFIL UTAMA</span>
                    <h4 className="text-xl font-bold text-white">Pia Lestari Heritage & Creative</h4>
                  </div>
                </div>
              </div>
            </div>

            <div className="lg:col-span-7">
              <span className="text-[#ff7a00] text-xs font-semibold uppercase tracking-widest block mb-3">LATAR BELAKANG KELUARGA</span>
              <h2 className="text-3xl md:text-4xl font-bold text-white mb-6 font-serif">Konsistensi & Semangat Kerja Keras</h2>
              <p className="text-zinc-300 text-lg leading-relaxed mb-6">
                Arsya Zain Nurrafif lahir di Pacitan pada 19 Januari 2008 sebagai anak bungsu dari tiga bersaudara dari pasangan Bapak Agus Wahyudin dan Ibu Surip Lestari. Kedua orang tuanya adalah wirausahawan mandiri yang memproduksi bakpia dengan brand <strong className="text-white font-semibold">"PIA LESTARI"</strong> di Dusun Klisat, Tambakrejo, Pacitan.
              </p>
              <p className="text-zinc-400 leading-relaxed mb-6">
                Sejak kelas 4 Sekolah Dasar hingga kini berada di bangku akhir MAN Pacitan, Arsya konsisten membantu usaha keluarga—mulai dari meracik adonan, membuat kue, hingga membungkus roti. Nilai kerja keras ini membentuk karakter disiplin dan tangguh dalam dirinya.
              </p>
              <div className="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-4 border-t border-white/10">
                <div>
                  <span className="text-zinc-500 text-xs block mb-1">TEMPAT, TANGGAL LAHIR</span>
                  <span className="text-white font-medium">Pacitan, 19 Januari 2008</span>
                </div>
                <div>
                  <span className="text-zinc-500 text-xs block mb-1">PENDIDIKAN SAAT INI</span>
                  <span className="text-white font-medium">MAN Pacitan (Kelas XII)</span>
                </div>
              </div>
            </div>
          </div>

          {/* Skills & Passions Grid */}
          <div className="mt-16">
            <div className="text-center max-w-2xl mx-auto mb-16">
              <span className="text-[#ff7a00] text-xs font-semibold uppercase tracking-widest block mb-2">KEAHLIAN & MINAT</span>
              <h3 className="text-3xl font-bold text-white font-serif">Bakat & Bidang Keahlian</h3>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
              
              {/* Skill 1 */}
              <div className="bg-zinc-900/60 border border-white/10 rounded-2xl p-8 hover:border-[#ff7a00]/50 transition-all duration-300 group">
                <div className="w-14 h-14 rounded-xl bg-[#ff7a00]/10 border border-[#ff7a00]/30 flex items-center justify-center text-[#ff7a00] mb-6 group-hover:scale-110 transition-transform">
                  <Music size={26} />
                </div>
                <h4 className="text-xl font-bold text-white mb-3">Seni Musik</h4>
                <p className="text-zinc-400 text-sm leading-relaxed">
                  Belajar secara otodidak terinspirasi dari sang ayah yang juga pembuat alat musik tradisional. Aktif mengembangkan bakat melalui ekstrakurikuler musik dan panggung sekolah.
                </p>
              </div>

              {/* Skill 2 */}
              <div className="bg-zinc-900/60 border border-white/10 rounded-2xl p-8 hover:border-[#ff7a00]/50 transition-all duration-300 group">
                <div className="w-14 h-14 rounded-xl bg-[#ff7a00]/10 border border-[#ff7a00]/30 flex items-center justify-center text-[#ff7a00] mb-6 group-hover:scale-110 transition-transform">
                  <Cpu size={26} />
                </div>
                <h4 className="text-xl font-bold text-white mb-3">Teknologi & Jaringan</h4>
                <p className="text-zinc-400 text-sm leading-relaxed">
                  Mendalami Teknik Komputer dan Jaringan (TKJ), instalasi Wi-Fi, topologi jaringan, serta merakit perangkat elektronik dan tata suara (sound system).
                </p>
              </div>

              {/* Skill 3 */}
              <div className="bg-zinc-900/60 border border-white/10 rounded-2xl p-8 hover:border-[#ff7a00]/50 transition-all duration-300 group">
                <div className="w-14 h-14 rounded-xl bg-[#ff7a00]/10 border border-[#ff7a00]/30 flex items-center justify-center text-[#ff7a00] mb-6 group-hover:scale-110 transition-transform">
                  <Camera size={26} />
                </div>
                <h4 className="text-xl font-bold text-white mb-3">Media Kreatif</h4>
                <p className="text-zinc-400 text-sm leading-relaxed">
                  Anggota aktif Tim Media Madrasah MAN Pacitan (Kelas 10 & 11). Menguasai fotografi, videografi, serta editing foto dan video profesional.
                </p>
              </div>

            </div>
          </div>

        </div>
      </section>

      {/* TIMELINE OF EXPERIENCE SECTION */}
      <section id="timeline" className="py-24 bg-[#0a0a0a] border-b border-white/5">
        <div className="max-w-7xl mx-auto px-6">
          
          <div className="flex flex-col md:flex-row md:items-end justify-between mb-16">
            <div>
              <span className="text-[#ff7a00] text-xs font-semibold uppercase tracking-widest block mb-2">JEJAK PENDIDIKAN & ORGANISASI</span>
              <h2 className="text-3xl md:text-4xl font-bold text-white font-serif">Timeline of experience</h2>
            </div>
            <p className="text-zinc-400 max-w-md mt-4 md:mt-0 text-sm">
              Perjalanan akademik, keaktifan organisasi, dan pencapaian Arsya Zain Nurrafif dari masa ke masa.
            </p>
          </div>

          {/* Timeline Brands / Milestone Bar style matching the reference */}
          <div className="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-4 mb-16">
            
            <div className="bg-zinc-900/80 border border-white/10 rounded-xl p-5 hover:border-[#ff7a00]/40 transition-colors">
              <span className="text-[#ff7a00] font-bold text-xs block mb-2">SDN 1 TAMBAKREJO</span>
              <p className="text-zinc-300 text-xs font-medium">Pendidikan Dasar & Memulai Wirausaha Kue Pia bersama Keluarga</p>
            </div>

            <div className="bg-zinc-900/80 border border-white/10 rounded-xl p-5 hover:border-[#ff7a00]/40 transition-colors">
              <span className="text-[#ff7a00] font-bold text-xs block mb-2">MTs ATTARMASIE</span>
              <p className="text-zinc-300 text-xs font-medium">Eksplorasi awal bidang teknik elektronika & sistem suara</p>
            </div>

            <div className="bg-zinc-900/80 border border-white/10 rounded-xl p-5 hover:border-[#ff7a00]/40 transition-colors">
              <span className="text-[#ff7a00] font-bold text-xs block mb-2">MAN PACITAN</span>
              <p className="text-zinc-300 text-xs font-medium">Tim Media Madrasah (Fotografi & Videografi)</p>
            </div>

            <div className="bg-zinc-900/80 border border-white/10 rounded-xl p-5 hover:border-[#ff7a00]/40 transition-colors">
              <span className="text-[#ff7a00] font-bold text-xs block mb-2">SAKA BHAYANGKARA</span>
              <p className="text-zinc-300 text-xs font-medium">Dipercaya mengemban amanah sebagai Ketua 1 Organisasi</p>
            </div>

            <div className="bg-zinc-900/80 border border-white/10 rounded-xl p-5 hover:border-[#ff7a00]/40 transition-colors col-span-2 sm:col-span-1">
              <span className="text-[#ff7a00] font-bold text-xs block mb-2">SAAT INI (KELAS XII)</span>
              <p className="text-zinc-300 text-xs font-medium">Fokus menyelesaikan studi akhir dengan prestasi membanggakan</p>
            </div>

          </div>

          {/* Large Featured Photo Banners incorporating user images */}
          <div className="space-y-8">
            <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[360px] md:h-[460px] bg-zinc-900 group">
              <div className="absolute inset-0 bg-gradient-to-tr from-black/80 via-black/40 to-transparent z-10"></div>
              <img 
                src="IMG-20251214-WA0276.jpg" 
                alt="Arsya Achievement" 
                className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
              />
              <div className="absolute bottom-6 left-6 right-6 z-20 text-center md:text-left">
                <div className="inline-block px-3 py-1 rounded-full bg-[#ff7a00]/20 border border-[#ff7a00]/40 text-[#ff7a00] text-xs font-semibold mb-2 uppercase">PRESTASI & AKTIVITAS</div>
                <h3 className="text-2xl md:text-3xl font-bold text-white mb-1">Aktivitas Kreatif & Juara Madrasah</h3>
                <p className="text-zinc-200 text-sm max-w-lg">Mengabadikan momen penting dan menorehkan prestasi membanggakan bersama rekan-rekan.</p>
              </div>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
              
              <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[320px] bg-zinc-900 group">
                <img src="IMG-20261017-WA0121.jpg" alt="Fire attraction" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"></div>
                <div className="absolute bottom-6 left-6 right-6 z-20">
                  <h4 className="text-xl font-bold text-white mb-1">Saka Bhayangkara</h4>
                  <p className="text-zinc-300 text-xs">Ketua 1 Organisasi, kepemimpinan & aksiatraktif.</p>
                </div>
              </div>

              <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[320px] bg-zinc-900 group">
                <img src="IMG-20261027-WA0117.jpg" alt="Music Performance" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"></div>
                <div className="absolute bottom-6 left-6 right-6 z-20">
                  <h4 className="text-xl font-bold text-white mb-1">Seni Musik & Band</h4>
                  <p className="text-zinc-300 text-xs">Bermain alat musik dan tampil percaya diri di atas panggung.</p>
                </div>
              </div>

              <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[320px] bg-zinc-900 group">
                <img src="IMG-20260403-WA0117.jpg" alt="Otomotif & Motor" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"></div>
                <div className="absolute bottom-6 left-6 right-6 z-20">
                  <h4 className="text-xl font-bold text-white mb-1">Otomotif & Hobi</h4>
                  <p className="text-zinc-300 text-xs">Keterampilan otomotif dan hobi berkendara mandiri.</p>
                </div>
              </div>

            </div>

            {/* Additional Photo Gallery Grid */}
            <div className="grid grid-cols-1 md:grid-cols-2 gap-8 pt-4">
              <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[300px] bg-zinc-900 group">
                <img src="IMG-20260323-WA0061.jpg" alt="At cafe" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                <div className="absolute bottom-6 left-6 z-20">
                  <h4 className="text-lg font-bold text-white">Momen Kreatif & Santai</h4>
                  <p className="text-zinc-400 text-xs">Eksplorasi tempat dan produksi konten media.</p>
                </div>
              </div>

              <div className="relative rounded-3xl overflow-hidden border border-white/10 h-[300px] bg-zinc-900 group">
                <img src="IMG-20261012-WA0026.jpg" alt="Casual portrait" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                <div className="absolute bottom-6 left-6 z-20">
                  <h4 className="text-lg font-bold text-white">Karakter & Semangat Muda</h4>
                  <p className="text-zinc-400 text-xs">Selalu siap menghadapi tantangan baru.</p>
                </div>
              </div>
            </div>

          </div>

        </div>
      </section>

      {/* CONTACT & CONNECT SECTION */}
      <section id="contact" className="py-24 bg-[#0d0d0d] relative">
        <div className="max-w-7xl mx-auto px-6">
          <div className="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
            
            {/* Left Column - Image / Visual representation */}
            <div className="lg:col-span-5">
              <div className="relative rounded-3xl overflow-hidden border border-white/10 bg-zinc-900 p-3 shadow-2xl">
                <div className="h-[420px] rounded-2xl overflow-hidden relative">
                  <img src="IMG-20261027-WA0115.jpg" alt="Mirror selfie camera" className="w-full h-full object-cover" />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#0d0d0d] via-black/40 to-transparent"></div>
                  <div className="absolute bottom-6 left-6 right-6 z-10">
                    <span className="text-[#ff7a00] text-xs font-semibold tracking-wider uppercase mb-2 block">MARI TERHUBUNG</span>
                    <h3 className="text-2xl font-bold text-white mb-2">Kunjungi Sosial Media</h3>
                    <p className="text-zinc-300 text-xs mb-4">Terhubung langsung dengan Arsya melalui platform berikut:</p>
                    
                    <div className="flex flex-col gap-2.5">
                      <a 
                        href="https://www.instagram.com/arsya.rafif?psln=MWh1bjhlMnU0MTViOQ==" 
                        target="_blank" 
                        rel="noreferrer"
                        className="px-4 py-2.5 rounded-xl bg-zinc-900/90 border border-white/10 hover:border-[#ff7a00] text-white text-xs font-medium flex items-center justify-between transition-all"
                      >
                        <span className="flex items-center gap-2"><Instagram size={16} className="text-[#ff7a00]" /> Instagram Arsya</span>
                        <ChevronRight size={14} className="text-zinc-500" />
                      </a>
                      <a 
                        href="https://www.tiktok.com/@arsya_zannrrff?_r=1&_t=ZS-9AuEGpKOGqS" 
                        target="_blank" 
                        rel="noreferrer"
                        className="px-4 py-2.5 rounded-xl bg-zinc-900/90 border border-white/10 hover:border-[#ff7a00] text-white text-xs font-medium flex items-center justify-between transition-all"
                      >
                        <span className="flex items-center gap-2"><Video size={16} className="text-[#ff7a00]" /> TikTok @arsya_zannrrff</span>
                        <ChevronRight size={14} className="text-zinc-500" />
                      </a>
                      <a 
                        href="https://wa.me/qr/ADU7H25XOS33E1" 
                        target="_blank" 
                        rel="noreferrer"
                        className="px-4 py-2.5 rounded-xl bg-[#25D366]/20 border border-[#25D366]/40 hover:bg-[#25D366]/30 text-[#25D366] text-xs font-medium flex items-center justify-between transition-all"
                      >
                        <span className="flex items-center gap-2"><MessageCircle size={16} /> WhatsApp Chat</span>
                        <ChevronRight size={14} className="text-[#25D366]" />
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            {/* Right Column - Contact Form matching reference style */}
            <div className="lg:col-span-7">
              <h2 className="text-3xl md:text-4xl font-bold text-white mb-4 font-serif">
                Want to connect with Arsya? Use the form below to send a personal message.
              </h2>
              <p className="text-zinc-400 mb-8 text-sm">
                Isi form di bawah ini dengan lengkap dan Arsya akan segera merespons pesan atau keperluan kolaborasi Anda.
              </p>

              {submitted ? (
                <div className="bg-[#ff7a00]/10 border border-[#ff7a00]/30 rounded-2xl p-6 text-center text-[#ff7a00] flex items-center justify-center gap-3">
                  <CheckCircle2 size={24} />
                  <span className="font-semibold">Pesan berhasil terkirim! Terima kasih telah menghubungi.</span>
                </div>
              ) : (
                <form onSubmit={handleSubmit} className="space-y-6">
                  <div>
                    <label className="block text-xs font-semibold text-zinc-400 uppercase tracking-wider mb-2">Email</label>
                    <input 
                      type="email" 
                      required
                      placeholder="arsyazain@gmail.com" 
                      value={formData.email}
                      onChange={(e) => setFormData({...formData, email: e.target.value})}
                      className="w-full bg-zinc-900 border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-zinc-600 focus:outline-none focus:border-[#ff7a00] transition-colors text-sm"
                    />
                  </div>

                  <div>
                    <label className="block text-xs font-semibold text-zinc-400 uppercase tracking-wider mb-2">Full Name</label>
                    <input 
                      type="text" 
                      required
                      placeholder="Nama Lengkap Anda" 
                      value={formData.name}
                      onChange={(e) => setFormData({...formData, name: e.target.value})}
                      className="w-full bg-zinc-900 border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-zinc-600 focus:outline-none focus:border-[#ff7a00] transition-colors text-sm"
                    />
                  </div>

                  <div>
                    <label className="block text-xs font-semibold text-zinc-400 uppercase tracking-wider mb-2">Message</label>
                    <textarea 
                      rows={4}
                      required
                      placeholder="Tulis pesan atau keperluan kolaborasi di sini..." 
                      value={formData.message}
                      onChange={(e) => setFormData({...formData, message: e.target.value})}
                      className="w-full bg-zinc-900 border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-zinc-600 focus:outline-none focus:border-[#ff7a00] transition-colors text-sm resize-none"
                    ></textarea>
                  </div>

                  <button 
                    type="submit"
                    className="px-8 py-4 rounded-full bg-[#ff7a00] hover:bg-[#e06c00] text-white font-semibold transition-all duration-300 shadow-lg shadow-[#ff7a00]/20 flex items-center justify-center gap-2 w-full sm:w-auto"
                  >
                    Contact Me <Send size={16} />
                  </button>
                </form>
              )}
            </div>

          </div>
        </div>
      </section>

      {/* FOOTER */}
      <footer className="bg-black border-t border-white/10 py-12">
        <div className="max-w-7xl mx-auto px-6 flex flex-col md:flex-row items-center justify-between gap-6">
          
          <div className="flex items-center gap-2">
            <span className="text-xl font-bold tracking-tight text-white font-serif">
              ARSYA ZAIN NURRAFIF<span className="text-[#ff7a00]">.</span>
            </span>
          </div>

          <div className="flex items-center gap-6 text-sm text-zinc-400">
            <button onClick={() => scrollToSection('home')} className="hover:text-[#ff7a00] transition-colors">Home</button>
            <button onClick={() => scrollToSection('bio')} className="hover:text-[#ff7a00] transition-colors">Bio</button>
            <button onClick={() => scrollToSection('timeline')} className="hover:text-[#ff7a00] transition-colors">Timeline</button>
            <button onClick={() => scrollToSection('contact')} className="hover:text-[#ff7a00] transition-colors">Contact</button>
          </div>

          <div className="flex items-center gap-4">
            <a href="https://www.instagram.com/arsya.rafif?psln=MWh1bjhlMnU0MTViOQ==" target="_blank" rel="noreferrer" className="text-zinc-400 hover:text-[#ff7a00] transition-colors" title="Instagram">
              <Instagram size={18} />
            </a>
            <a href="https://www.tiktok.com/@arsya_zannrrff?_r=1&_t=ZS-9AuEGpKOGqS" target="_blank" rel="noreferrer" className="text-zinc-400 hover:text-[#ff7a00] transition-colors" title="TikTok">
              <Video size={18} />
            </a>
            <a href="https://wa.me/qr/ADU7H25XOS33E1" target="_blank" rel="noreferrer" className="text-zinc-400 hover:text-[#25D366] transition-colors" title="WhatsApp">
              <MessageCircle size={18} />
            </a>
          </div>

          <button 
            onClick={() => scrollToSection('home')}
            className="w-10 h-10 rounded-full bg-zinc-900 border border-white/10 flex items-center justify-center text-zinc-400 hover:text-white hover:border-[#ff7a00] transition-all"
            aria-label="Back to top"
          >
            <ArrowUp size={16} />
          </button>

        </div>
        <div className="max-w-7xl mx-auto px-6 mt-8 pt-8 border-t border-white/5 text-center text-xs text-zinc-600">
          © {new Date().getFullYear()} Arsya Zain Nurrafif. All rights reserved. Built with Next.js & Tailwind CSS.
        </div>
      </footer>

    </div>
  );
}
