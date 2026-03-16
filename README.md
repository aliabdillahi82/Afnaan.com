!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Afnaan - Personal Website</title>

<style>
* { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior: smooth; }
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background:#f9f9f9; color:#333; line-height:1.6; }

header {
  background: linear-gradient(to right, #4a90e2, #357ab8);
  color:white; padding:60px 20px; text-align:center;
}
header h1 { font-size:3em; margin-bottom:10px; }
header p { font-size:1.2em; opacity:0.9; }

nav {
  background:#2c3e50; display:flex; justify-content:center; flex-wrap:wrap;
  position:sticky; top:0; z-index:1000;
}
nav a { color:white; text-decoration:none; margin:10px 20px; font-weight:bold; padding-bottom:5px; transition: color 0.3s, border-bottom 0.3s; }
nav a.active { border-bottom:3px solid #4a90e2; }
nav a:hover { color:#4a90e2; }

section { padding:80px 20px; text-align:center; max-width:1200px; margin:auto; }
section:nth-of-type(odd){ background:#fff; }
section:nth-of-type(even){ background:#f1f1f1; }
h2{ font-size:2.5em; margin-bottom:20px; color:#2c3e50; }
p{ font-size:1.1em; max-width:700px; margin:auto; }

.filter-btns { margin-bottom:20px; display:flex; justify-content:center; flex-wrap:wrap; gap:10px; }
.filter-btns button {
  background:#f1f1f1; border:1px solid #ccc; color:#333; padding:10px 20px; border-radius:6px;
  cursor:pointer; font-weight:bold; transition: all 0.3s;
}
.filter-btns button.active, .filter-btns button:hover {
  background:#007bff; color:white; border-color:#007bff;
}

.portfolio {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}
.card {
  background:white; border-radius:12px; padding:20px;
  box-shadow:0 4px 15px rgba(0,0,0,0.1); transition: transform 0.3s, box-shadow 0.3s, opacity 0.5s;
  text-decoration:none; color:inherit; display:block; opacity:1; transform:translateY(0);
}
.card.hide { opacity:0; transform:translateY(20px); pointer-events:none; }
.card.hidden { display:none; }
.card:hover { transform:translateY(-10px); box-shadow:0 10px 25px rgba(0,0,0,0.2); }
.card img, .card iframe { width:100%; border-radius:8px; margin-bottom:15px; }
.card h3 { font-size:1.3em; margin-bottom:8px; }
.card p { font-size:1em; color:#555; }

#loadMore {
  margin-top:20px; padding:12px 25px; font-weight:bold;
  background:#007bff; color:white; border:none; border-radius:5px; cursor:pointer; transition: background 0.3s;
}
#loadMore:hover { background:#0056b3; }

footer { background:#2c3e50; color:white; text-align:center; padding:30px 20px; }

@media (max-width:768px) { header h1{ font-size:2.2em; } h2{ font-size:2em; } }
</style>
</head>

<body>

<header id="home">
  <h1>Afnaan</h1>
  <p>Welcome to my personal website</p>
</header>

<nav>
  <a href="#home" class="nav-link active">Home</a>
  <a href="#about" class="nav-link">About</a>
  <a href="#work" class="nav-link">Work</a>
  <a href="#contact" class="nav-link">Contact</a>
</nav>

<section id="about">
  <h2>About Me</h2>
  <p>Hello! My name is Afnaan. This is my personal website where I share my work, ideas, and projects. I enjoy creating meaningful content and building useful tools for people.</p>
</section>

<section id="work">
  <h2>My Work</h2>

  <div class="filter-btns">
    <button onclick="filterSelection('all')" class="active">All</button>
    <button onclick="filterSelection('project')">Projects</button>
    <button onclick="filterSelection('video')">Videos</button>
    <button onclick="filterSelection('link')">Links</button>
  </div>

  <div class="portfolio">
    <a href="https://example.com/project1" target="_blank" class="card project">
      <img src="https://via.placeholder.com/300x180" alt="Project One">
      <h3>Project One</h3>
      <p>A clickable project link.</p>
    </a>

    <div class="card video">
      <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="Video Project" frameborder="0" allowfullscreen></iframe>
      <h3>Video Project</h3>
      <p>Watch this video project.</p>
    </div>

    <a href="https://example.com/project2" target="_blank" class="card project">
      <img src="https://via.placeholder.com/300x180" alt="Project Two">
      <h3>Project Two</h3>
      <p>Another project link.</p>
    </a>

    <a href="https://example.com/business" target="_blank" class="card link">
      <img src="https://via.placeholder.com/300x180" alt="Business Link">
      <h3>Business Link</h3>
      <p>Visit this business website.</p>
    </a>

    <a href="https://example.com/project3" target="_blank" class="card project hidden">
      <img src="https://via.placeholder.com/300x180" alt="Project Three">
      <h3>Project Three</h3>
      <p>Another project link to load.</p>
    </a>

    <div class="card video hidden">
      <iframe src="https://www.youtube.com/embed/9bZkp7q19f0" title="Video Project 2" frameborder="0" allowfullscreen></iframe>
      <h3>Video Project 2</h3>
      <p>Another video project to load.</p>
    </div>
  </div>

  <button id="loadMore">Load More</button>
</section>

<section id="contact">
  <h2>Contact</h2>
  <p>Email: <a href="mailto:your@email.com" style="color:#007bff;">your@email.com</a></p>
</section>

<footer>
  <p>© 2026 Afnaan</p>
</footer>

<script>
function filterSelection(category) {
  let cards = document.querySelectorAll('.portfolio .card');
  cards.forEach(card => {
    if(category === 'all' || card.classList.contains(category)) {
      card.classList.remove('hide'); 
      if(card.classList.contains('hidden')) card.style.display='none';
    } else card.classList.add('hide');
  });

  document.querySelectorAll('.filter-btns button').forEach(btn => btn.classList.remove('active'));
  event.target.classList.add('active');
}

document.getElementById('loadMore').addEventListener('click', () => {
  let hiddenCards = document.querySelectorAll('.portfolio .hidden');
  hiddenCards.forEach(card => {
    card.style.display='block';
    card.classList.remove('hidden');
    setTimeout(() => card.classList.remove('hide'), 50);
  });
  document.getElementById('loadMore').style.display='none';
});

const sections = document.querySelectorAll('section, header');
const navLinks = document.querySelectorAll('nav a');

window.addEventListener('scroll', () => {
  let scrollPos = window.scrollY + 100;
  sections.forEach(sec => {
    if(scrollPos >= sec.offsetTop && scrollPos < sec.offsetTop + sec.offsetHeight){
      navLinks.forEach(link => link.classList.remove('active'));
      let current = sec.id || 'home';
      document.querySelector(`nav a[href="#${current}"]`).classList.add('active');
    }
  });
});
</script>

</body>
</html>
