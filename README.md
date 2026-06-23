// Smooth scrolling
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
            target.scrollIntoView({
                behavior: 'smooth',
                block: 'start'
            });
        }
    });
});

// Quote Form submission
document.querySelector('.quote-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const name = this.querySelector('input[type="text"]').value;
    const email = this.querySelector('input[type="email"]').value;
    const phone = this.querySelector('input[type="tel"]').value;
    const service = this.querySelector('select').value;
    
    alert(`Thank you ${name}! We received your free quote request for ${service}. We'll contact you at ${phone} within 24 hours!`);
    this.reset();
});

// Contact Form submission
document.querySelector('.contact-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const name = this.querySelector('input[type="text"]').value;
    alert(`Thank you ${name}! We'll get back to you soon!`);
    this.reset();
});

// Navbar background on scroll
window.addEventListener('scroll', () => {
    const navbar = document.querySelector('.navbar');
    if (window.scrollY > 50) {
        navbar.style.boxShadow = '0 10px 30px rgba(30, 90, 150, 0.3)';
    } else {
        navbar.style.boxShadow = '0 10px 30px rgba(30, 90, 150, 0.2)';
    }
});

// Add animation on scroll
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -100px 0px'
};

const observer = new IntersectionObserver(function(entries) {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        }
    });
}, observerOptions);

document.querySelectorAll('.service-card, .review-card, .reason-card').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'all 0.6s ease-out';
    observer.observe(el);
});

// Mobile menu toggle
const navLinks = document.querySelector('.nav-links');
if (navLinks) {
    document.addEventListener('click', function(e) {
        if (window.innerWidth <= 768 && !e.target.closest('.nav-brand') && !e.target.closest('.nav-links')) {
            navLinks.style.display = 'none';
        }
    });
}
