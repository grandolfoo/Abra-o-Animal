<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abraço Animal | Proteção e Amor</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Open+Sans:wght@300;400;600&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/scrollreveal"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

    <style>
        :root {
            --primary: #f38d1e;
            --primary-dark: #d37610;
            --secondary: #603813;
            --bg-body: #fdfaf5;
            --white: #ffffff;
            --glass: rgba(255, 255, 255, 0.8);
            --transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--bg-body);
            color: var(--secondary);
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        h1, h2, h3, .logo { font-weight: 700; }

        /* Container global para evitar esticar demais em TVs */
        .container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
        }

        /* --- Custom Scrollbar --- */
        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: var(--bg-body); }
        ::-webkit-scrollbar-thumb { background: var(--primary); border-radius: 5px; }

        /* --- Header & Nav --- */
        header {
            position: fixed; 
            width: 100%; 
            top: 0; 
            z-index: 2000;
            padding: 20px 8%; 
            display: flex; 
            justify-content: space-between; 
            align-items: center;
            transition: var(--transition);
            background: rgba(0, 0, 0, 0.3);
        }

        header.scrolled {
            background: var(--white);
            padding: 15px 8%;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .logo-container a {
            display: flex;
            align-items: center;
            position: relative;
            height: 50px;
        }

        .logo-img {
            height: 70px;
            width: auto;
            transition: var(--transition);
        }

        .logo-branca { opacity: 1; visibility: visible; }
        .logo-laranja { position: absolute; left: 0; opacity: 0; visibility: hidden; }

        header.scrolled .logo-branca { opacity: 0; visibility: hidden; }
        header.scrolled .logo-laranja { opacity: 1; visibility: visible; }
        header.scrolled .logo-img { height: 60px; }

        /* Navigation Menu */
        nav ul { 
            display: flex; 
            list-style: none; 
            gap: 30px; 
            align-items: center;
        }
        
        nav a { 
            text-decoration: none; 
            color: var(--white); 
            font-weight: 600; 
            font-size: 1.05rem; 
            transition: var(--transition);
        }

        nav a:hover { color: var(--primary); }
        header.scrolled nav a { color: var(--secondary); }
        header.scrolled nav a:hover { color: var(--primary); }

        /* Botão do Menu Mobile */
        .mobile-toggle {
            display: none;
            background: none;
            border: none;
            color: var(--white);
            font-size: 1.8rem;
            cursor: pointer;
            z-index: 2100;
        }
        header.scrolled .mobile-toggle { color: var(--secondary); }

        /* --- Hero Section --- */
        .hero {
            min-height: 100vh;
            padding: 120px 20px 60px;
            background: linear-gradient(135deg, rgba(0,0,0,0.6), rgba(0,0,0,0.3)), 
                        url('https://images.unsplash.com/photo-1544568100-847a948585b9?q=80&w=1974') center/cover no-repeat;
            display: flex; 
            flex-direction: column; 
            justify-content: center; 
            align-items: center;
            color: var(--white); 
            text-align: center; 
            clip-path: ellipse(150% 100% at 50% 0%);
        }

        .hero h1 { font-size: clamp(2.2rem, 5vw, 4.5rem); margin-bottom: 20px; line-height: 1.2; }
        .hero p { font-size: clamp(1rem, 2vw, 1.5rem); margin-bottom: 30px; font-weight: 300; max-width: 700px; }

        .btn-cta {
            padding: 15px 40px; 
            background: var(--primary); 
            color: var(--white);
            border: none; 
            border-radius: 50px; 
            font-size: 1.1rem; 
            font-weight: 700;
            cursor: pointer; 
            transition: var(--transition); 
            box-shadow: 0 10px 20px rgba(243, 141, 30, 0.3);
        }
        .btn-cta:hover { 
            transform: translateY(-3px); 
            box-shadow: 0 15px 25px rgba(243, 141, 30, 0.5); 
            background: var(--primary-dark); 
        }

        /* --- Section Styling --- */
        .section-padding { padding: 80px 8%; }

        .filter-buttons { 
            display: flex; 
            justify-content: center; 
            flex-wrap: wrap; 
            gap: 12px; 
            margin-bottom: 40px; 
        }

        .filter-btn {
            padding: 10px 25px; 
            border: 2px solid var(--primary); 
            border-radius: 25px;
            background: transparent; 
            color: var(--primary); 
            font-weight: 700; 
            cursor: pointer; 
            transition: var(--transition);
        }
        .filter-btn.active, .filter-btn:hover { background: var(--primary); color: var(--white); }

        /* --- Grid de Animais --- */
        .pets-grid {
            display: grid; 
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); 
            gap: 30px;
        }

        .pet-card {
            background: var(--white); 
            border-radius: 20px; 
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.05); 
            transition: var(--transition);
            position: relative; 
            border: 1px solid rgba(0,0,0,0.05);
            display: flex;
            flex-direction: column;
        }

        .pet-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px rgba(0,0,0,0.1); }
        .pet-img { width: 100%; height: 260px; object-fit: cover; }
        .pet-info { padding: 25px; display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between; }
        .pet-info h3 { font-size: 1.5rem; margin-bottom: 8px; }
        .pet-info p { margin-bottom: 15px; font-size: 0.95rem; color: #666; }
        
        .pet-tag { 
            position: absolute; 
            top: 15px; 
            right: 15px; 
            background: var(--primary); 
            color: white; 
            padding: 5px 15px; 
            border-radius: 15px; 
            font-size: 0.8rem; 
            font-weight: 700;
        }

        /* --- Tabela de Rotina --- */
        .routine-box {
            background: var(--white); 
            border-radius: 20px; 
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08); 
            border: 1px solid #eee;
            max-width: 900px;
            margin: 0 auto;
        }
        .routine-row {
            display: grid; 
            grid-template-columns: 180px 1fr; 
            border-bottom: 1px solid #f0f0f0;
            transition: var(--transition);
        }
        .routine-row:last-child { border-bottom: none; }
        .routine-row:hover { background: #fffcf7; }
        .time-cell { background: var(--secondary); color: var(--primary); padding: 18px 20px; font-weight: 700; display: flex; align-items: center; }
        .task-cell { padding: 18px 20px; display: flex; align-items: center; font-weight: 500; }

        /* --- Modal de Detalhes --- */
        .modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); display: none; justify-content: center;
            align-items: center; z-index: 3000; backdrop-filter: blur(5px);
            padding: 20px;
        }
        .modal-content {
            background: var(--white); padding: 40px 30px; border-radius: 25px;
            max-width: 500px; width: 100%; text-align: center; position: relative;
        }
        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #888; }

        /* --- Footer --- */
        footer {
            background: var(--secondary);
            color: #fff;
            padding: 80px 8% 40px;
            position: relative;
            overflow: hidden;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 40px;
            position: relative;
            z-index: 2;
            max-width: 1400px;
            margin: 0 auto;
        }

        .footer-content h3, .footer-content h4 { margin-bottom: 15px; }
        .footer-content p { margin-bottom: 10px; font-size: 0.95rem; opacity: 0.9; }

        .social-icons {
            display: flex; gap: 15px; font-size: 1.5rem; margin-top: 15px;
        }
        .social-icons i { cursor: pointer; transition: var(--transition); }
        .social-icons i:hover { color: var(--primary); }

        .paw {
            position: absolute;
            width: 150px;
            z-index: 1;
            pointer-events: none;
            opacity: 0.2;
        }

        .paw-left-bottom { right: 5%; bottom: 10px; }

        .footer-bottom {
            text-align: center; 
            margin-top: 60px; 
            opacity: .6; 
            font-size: .85rem;
            position: relative;
            z-index: 2;
        }

        /* --- RESPONSIVIDADE (MEDIA QUERIES) --- */

        /* Telas Ultra Laranjas e TVs (>= 1600px) */
        @media (min-width: 1600px) {
            .hero h1 { font-size: 5rem; }
            .hero p { font-size: 1.8rem; }
            .section-padding { padding: 120px 12%; }
            .pets-grid { grid-template-columns: repeat(4, 1fr); }
        }

        /* Tablets e Telas Médias (<= 992px) */
        @media (max-width: 992px) {
            .mobile-toggle { display: block; }

            nav ul {
                position: fixed;
                top: 0; right: -100%;
                width: 70%; height: 100vh;
                background: var(--secondary);
                flex-direction: column;
                justify-content: center;
                transition: var(--transition);
                box-shadow: -5px 0 15px rgba(0,0,0,0.2);
            }

            nav.active ul { right: 0; }

            nav a { color: var(--white) !important; font-size: 1.2rem; }
            
            .pets-grid { grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); }
        }

        /* Celulares (<= 600px) */
        @media (max-width: 600px) {
            header { padding: 15px 5%; }
            .section-padding { padding: 60px 5%; }

            .hero { clip-path: none; } /* Remove corte para economizar espaço */

            .routine-row { grid-template-columns: 1fr; }
            .time-cell { background: var(--primary); color: var(--white); padding: 12px 15px; }
            .task-cell { padding: 15px; }

            .footer-content { grid-template-columns: 1fr; gap: 30px; text-align: center; }
            .social-icons { justify-content: center; }
            
            .paw-left-bottom { display: none; }
        }
    </style>
</head>
<body>

    <header id="navbar">
        <div class="logo-container">
            <a href="#inicio">
                <img src="Sem título-1.svg" alt="Logo Abraço Animal" class="logo-img logo-branca">
                <img src="logo vetorizada sem fundo (1).svg" alt="Logo Abraço Animal" class="logo-img logo-laranja">
            </a>
        </div>

        <button class="mobile-toggle" id="mobileToggle" aria-label="Abrir Menu">
            <i class="fas fa-bars"></i>
        </button>

        <nav id="navMenu">
            <ul>
                <li><a href="#inicio" onclick="closeNav()">Início</a></li>
                <li><a href="#adotar" onclick="closeNav()">Adoção</a></li>
                <li><a href="#rotina" onclick="closeNav()">Rotina</a></li>
                <li><a href="#contato" onclick="closeNav()">Contato</a></li>
            </ul>
        </nav>
    </header>

    <section id="inicio" class="hero">
        <h1 class="reveal">O amor não tem raça,<br>tem abraço.</h1>
        <p class="reveal">Resgatando vidas e criando novas histórias desde 2026.</p>
        <button class="btn-cta reveal" onclick="location.href='#adotar'">Encontrar um amigo</button>
    </section>

    <section id="adotar" class="section-padding container">
        <h2 style="text-align: center; margin-bottom: 10px; font-size: 2rem;">Nossos Protegidos</h2>
        <p style="text-align: center; margin-bottom: 40px;">Filtre por espécie e encontre sua alma gêmea.</p>
        
        <div class="filter-buttons">
            <button class="filter-btn active" onclick="filterPets('todos', event)">Todos</button>
            <button class="filter-btn" onclick="filterPets('cachorro', event)">Cachorros</button>
            <button class="filter-btn" onclick="filterPets('gato', event)">Gatos</button>
            <button class="filter-btn" onclick="filterPets('ouriço', event)">Ouriços</button>
            <button class="filter-btn" onclick="filterPets('papagaio', event)">Papagaios</button>
        </div>

        <div class="pets-grid" id="petsContainer">
            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://images.unsplash.com/photo-1583511655857-d19b40a7a54e?w=500" class="pet-img" alt="Tico">
                <div class="pet-info">
                    <h3>Tico</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte Pequeno</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Tico', 'Um cãozinho alegre e cheio de energia, resgatado na Zona Sul.')">Ver Dados</button>
                </div>
            </div>

            <div class="pet-card" data-type="gato">
                <span class="pet-tag">Gato</span>
                <img src="https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=500" class="pet-img" alt="Aurora">
                <div class="pet-info">
                    <h3>Aurora</h3>
                    <p><i class="fas fa-venus-mars"></i> Fêmea | <i class="fas fa-cat"></i> Filhote</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Aurora', 'Dócil e ronronante, adora um colo e sachê de salmão.')">Ver Dados</button>
                </div>
            </div>

            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://s2-globorural.glbimg.com/iZ0CNNZjGxlhpn6dp7SFJJQJn4I=/0x0:5200x3481/888x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_afe5c125c3bb42f0b5ae633b58923923/internal_photos/bs/2022/Z/M/KSqLB5RSag5QKidCPaaw/gettyimages-709130459.jpg" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Apollo</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte Grande</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>

             <div class="pet-card" data-type="gato">
                <span class="pet-tag">Gato</span>
                <img src="https://cantinhodosanimais.com.br/wordpress/wp-content/files/cantinhodosanimais.com.br/2025/12/brisht-shorthair-1024x683.webp" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Blaze</h3>
                    <p><i class="fas fa-venus-mars"></i> Femea | <i class="fas fa-dog"></i> Porte Grande</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
            <div class="pet-card" data-type="ouriço">
                <span class="pet-tag">Ouriço</span>
                <img src="https://www.phoenixzoo.org/wp-content/uploads/2024/03/DSC_6835-scaled.jpg" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Chuck</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte pequeno</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
            <div class="pet-card" data-type="papagaio">
                <span class="pet-tag">Papagaio</span>
                <img src="https://www.galaxcommerce.com.br/sistema/upload/3339/produtos/papagaio-verdadeiro-amazona-aestiva_2024-02-23_23-31-12_3_254.png" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Jet</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-bird"></i> Porte pequeno</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
             <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://p2.trrsf.com/image/fget/cf/1200/1200/middle/images.terra.com/2024/09/23/1726614881-cachorro-adocao.jpg" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Chip</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> filhote</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://i.pinimg.com/736x/4e/c0/0c/4ec00c75e56b79d456df24893bae7241.jpg" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Shadow</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> filhote</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://www.patasdacasa.com.br/sites/default/files/styles/article_detail_1200/public/2024-06/bull-terrier.jpg.webp?itok=X_-JN03E" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Brutos</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte Grande</p>
                    <button class="btn-cta" style="width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
        </div>
    </section>

    <section id="rotina" class="section-padding" style="background: #fdf2e9;">
        <div class="container">
            <h2 style="text-align: center; margin-bottom: 40px; font-size: 2rem;">Nossa Rotina de Excelência</h2>
            <div class="routine-box">
                <div class="routine-row">
                    <div class="time-cell">07:00 - 08:00</div>
                    <div class="task-cell">Alimentação, Hidratação e Cuidados iniciais</div>
                </div>
                <div class="routine-row">
                    <div class="time-cell">08:00 - 12:00</div>
                    <div class="task-cell">Resgates, acolhimentos e atendimentos emergenciais</div>
                </div>
                <div class="routine-row">
                    <div class="time-cell">12:00 - 13:00</div>
                    <div class="task-cell">Intervalo da equipe</div>
                </div>
                <div class="routine-row">
                    <div class="time-cell">13:00 - 15:00</div>
                    <div class="task-cell">Consultas veterinárias e tratamento dos animais</div>
                </div>
                <div class="routine-row">
                    <div class="time-cell">15:00 - 16:30</div>
                    <div class="task-cell">Atendimento ao público e processos de adoção</div>
                </div>
                <div class="routine-row">
                    <div class="time-cell">16:30 - 18:00</div>
                    <div class="task-cell">Produção de conteúdo, campanhas e conscientização</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal -->
    <div class="modal" id="petModal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal()">&times;</span>
            <h2 id="modalTitle">Nome do Pet</h2>
            <p id="modalDesc" style="margin: 20px 0; color: #666;"></p>
            <button class="btn-cta">Iniciar Processo de Adoção</button>
        </div>
    </div>

    <footer id="contato">    
        <div class="footer-content">
            <div>
                <h3 style="color: var(--primary);">Abraço Animal</h3>
                <p>Um trabalho acadêmico por Lucas, Maria Beatriz, Mateus Abreu, Matheus Lima e Sarah.</p>
            </div>

            <div>
                <h4>Contato</h4>
                <p><i class="fas fa-envelope"></i> abracoanimal@gmail.com</p>
                <p><i class="fas fa-phone"></i> (11) 12345-6789</p>
                <p><i class="fas fa-map-marker-alt"></i> Av. Paulista, 345 - SP</p>
            </div>

            <div>
                <h4>Social</h4>
                <div class="social-icons">
                    <i class="fab fa-instagram"></i>
                    <i class="fab fa-facebook"></i>
                    <i class="fas fa-envelope"></i>
                    <i class="fab fa-tiktok"></i>
                </div>
            </div>

            <img src="patinhas_V3.png" class="paw paw-left-bottom" alt="Patinhas da nossa logo">
        </div>

        <div class="footer-bottom">
            CNPJ: 12.345.657/8910-11 | © Abraço Animal 2026 | Todos os direitos reservados
        </div>
    </footer> 

    <script>
        // Header scroll behavior
        window.addEventListener('scroll', function() {
            const nav = document.getElementById('navbar');
            if (window.scrollY > 50) {
                nav.classList.add('scrolled');
            } else {
                nav.classList.remove('scrolled');
            }
        });

        // Toggle Menu Mobile
        const mobileToggle = document.getElementById('mobileToggle');
        const navMenu = document.getElementById('navMenu');

        mobileToggle.addEventListener('click', () => {
            navMenu.classList.toggle('active');
            const icon = mobileToggle.querySelector('i');
            if (navMenu.classList.contains('active')) {
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-times');
            } else {
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            }
        });

        function closeNav() {
            navMenu.classList.remove('active');
            const icon = mobileToggle.querySelector('i');
            icon.classList.remove('fa-times');
            icon.classList.add('fa-bars');
        }

        // Filtro de Animais
        function filterPets(type, event) {
            const cards = document.querySelectorAll('.pet-card');
            const btns = document.querySelectorAll('.filter-btn');
            
            btns.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

            cards.forEach(card => {
                if (type === 'todos' || card.getAttribute('data-type') === type) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }

        // Modal
        function openModal(name, desc) {
            document.getElementById('modalTitle').innerText = name;
            document.getElementById('modalDesc').innerText = desc;
            document.getElementById('petModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('petModal').style.display = 'none';
        }

        // Fechar Modal ao clicar fora
        window.onclick = function(event) {
            const modal = document.getElementById('petModal');
            if (event.target === modal) {
                closeModal();
            }
        }

        // ScrollReveal Animations
        ScrollReveal().reveal('.reveal', { 
            delay: 200, 
            distance: '30px', 
            origin: 'bottom', 
            interval: 150 
        });

        ScrollReveal().reveal('.pet-card', { 
            delay: 200, 
            interval: 100,
            scale: 0.95
        });
    </script>
</body>
</html>
