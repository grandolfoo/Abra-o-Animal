<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abraço Animal | Proteção e Amor</title>
    
    
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Open+Sans:wght@300;400;600&display=swap" rel="stylesheet">
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

        h1, h2, h3, .logo { font-family: 'Hobo Std', sans-serif; font-weight: 700; }

        /* --- Custom Scrollbar --- */
        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: var(--bg-body); }
        ::-webkit-scrollbar-thumb { background: var(--primary); border-radius: 5px; }

        /* --- Header & Nav (Atualizado para Links Brancos) --- */
        header {
            position: fixed; width: 100%; top: 0; z-index: 2000;
            padding: 40px 8%; display: flex; justify-content: space-between; align-items: center;
            transition: var(--transition);
            background: rgba(0, 0, 0, 0.2); /* Um fundo sutil escuro inicial para dar leitura ao branco */
        }

        /* Quando o usuário rolar a página, o fundo fica branco fosco */
        header.scrolled {
            background: var(--white);
            padding: 30px 8%;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        /* Logo começa branco e muda para laranja ao rolar */
        .logo-container a {
    display: flex;
    align-items: center;
    position: relative;
    height: 50px; /* Define uma altura fixa para o container */
}

/* Regra geral para as duas imagens de logo */
.logo-img {
    height: 100px; /* Altura padrão da logo */
    width: auto;
    transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
}

/* --- ESTADO INICIAL (Topo da página) --- */
.logo-branca {
    opacity: 1;
    visibility: visible;
}

.logo-laranja {
    position: absolute; /* Coloca a logo laranja exatamente atrás/atrás da branca */
    left: 0;
    opacity: 0;
    visibility: hidden;
}

/* --- ESTADO ROLADO (Quando o usuário desce a página) --- */
header.scrolled .logo-branca {
    opacity: 0;
    visibility: hidden;
}

header.scrolled .logo-laranja {
    opacity: 1;
    visibility: visible;
}

/* Opcional: Se quiser que a logo laranja fique ligeiramente menor ao rolar */
header.scrolled .logo-img {
    height: 90px;
}
        
        nav ul { display: flex; list-style: none; gap: 30px; }
        
        /* Links alterados de marrom para BRANCO por padrão */
        nav a { 
            text-decoration: none; 
            color: var(--white); 
            font-weight: 600; 
            font-size: 1.1rem; 
            transition: var(--transition);
        }

        /* Quando passa o mouse, muda para a cor primária (laranja) */
        nav a:hover { color: var(--primary); }

        /* Quando a página sofre scroll, os links mudam para marrom para não sumirem no fundo branco */
        header.scrolled nav a {
            color: var(--secondary);
        }
        header.scrolled nav a:hover {
            color: var(--primary);
        }

        /* --- Hero Section --- */
        .hero {
            height: 100vh;
            background: linear-gradient(135deg, rgba(0,0,0,0.5), rgba(0,0,0,0.2)), 
                        url('https://images.unsplash.com/photo-1544568100-847a948585b9?q=80&w=1974') center/cover;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            color: var(--white); text-align: center; clip-path: ellipse(150% 100% at 50% 0%);
        }

        .hero h1 { font-size: 4rem; margin-bottom: 20px; line-height: 1.1; }
        .hero p { font-size: 1.4rem; margin-bottom: 30px; font-weight: 300; }

        .btn-cta {
            padding: 15px 40px; background: var(--primary); color: var(--white);
            border: none; border-radius: 50px; font-size: 1.1rem; font-weight: 700;
            cursor: pointer; transition: var(--transition); box-shadow: 0 10px 20px rgba(243, 141, 30, 0.3);
        }
        .btn-cta:hover { transform: translateY(-3px); box-shadow: 0 15px 25px rgba(243, 141, 30, 0.5); background: var(--primary-dark); }

        /* --- Grid de Animais --- */
        .section-padding { padding: 100px 8%; }
        .filter-buttons { display: flex; justify-content: center; gap: 15px; margin-bottom: 50px; }
        .filter-btn {
            padding: 10px 25px; border: 2px solid var(--primary); border-radius: 25px;
            background: transparent; color: var(--primary); font-weight: 700; cursor: pointer; transition: var(--transition);
        }
        .filter-btn.active, .filter-btn:hover { background: var(--primary); color: var(--white); }

        .pets-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px;
        }

        .pet-card {
            background: var(--white); border-radius: 20px; overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.05); transition: var(--transition);
            position: relative; border: 1px solid rgba(0,0,0,0.05);
        }

        .pet-card:hover { transform: translateY(-10px); box-shadow: 0 20px 40px rgba(0,0,0,0.1); }
        .pet-img { width: 100%; height: 280px; object-fit: cover; }
        .pet-info { padding: 25px; }
        .pet-tag { 
            position: absolute; top: 15px; right: 15px; background: var(--primary); 
            color: white; padding: 5px 15px; border-radius: 15px; font-size: 0.8rem; font-weight: 700;
        }

        /* --- Tabela de Rotina --- */
        .routine-box {
            background: var(--white); border-radius: 30px; overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1); border: 1px solid #eee;
        }
        .routine-row {
            display: grid; grid-template-columns: 200px 1fr; border-bottom: 1px solid #f0f0f0;
            transition: var(--transition);
        }
        .routine-row:hover { background: #fffcf7; }
        .time-cell { background: var(--secondary); color: var(--primary); padding: 20px; font-weight: 700; }
        .task-cell { padding: 20px; align-self: center; font-weight: 500; }

        /* --- Modal de Detalhes --- */
        .modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); display: none; justify-content: center;
            align-items: center; z-index: 3000; backdrop-filter: blur(5px);
        }
        .modal-content {
            background: var(--white); padding: 40px; border-radius: 25px;
            max-width: 500px; width: 90%; text-align: center; position: relative;
        }
        .close-modal { position: absolute; top: 20px; right: 20px; font-size: 1.5rem; cursor: pointer; }

        footer { background: var(--secondary); color: var(--white); padding: 80px 8% 30px; }
        .footer-content { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 50px; }
        
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            .routine-row { grid-template-columns: 1fr; }
            nav { display: none; }
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
    <nav>
        <ul>
            <li><a href="#inicio">Início</a></li>
            <li><a href="#adotar">Adoção</a></li>
            <li><a href="#rotina">Rotina</a></li>
            <li><a href="#contato">Contato</a></li>
        </ul>
    </nav>
</header>

    <section id="inicio" class="hero">
        <h1 class="reveal">O amor não tem raça,<br>tem abraço.</h1>
        <p class="reveal">Resgatando vidas e criando novas histórias desde 2026.</p>
        <button class="btn-cta reveal" onclick="location.href='#adotar'">Encontrar um amigo</button>
    </section>

    <section id="adotar" class="section-padding">
        <h2 style="text-align: center; margin-bottom: 10px;">Nossos Protegidos</h2>
        <p style="text-align: center; margin-bottom: 40px;">Filtre por espécie e encontre sua alma gêmea.</p>
        
        <div class="filter-buttons">
            <button class="filter-btn active" onclick="filterPets('todos')">Todos</button>
            <button class="filter-btn" onclick="filterPets('cachorro')">Cachorros</button>
            <button class="filter-btn" onclick="filterPets('gato')">Gatos</button>
        </div>

        <div class="pets-grid" id="petsContainer">
            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="https://images.unsplash.com/photo-1583511655857-d19b40a7a54e?w=500" class="pet-img" alt="Tico">
                <div class="pet-info">
                    <h3>Tico</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte Pequeno</p>
                    <button class="btn-cta" style="margin-top:15px; width:100%" onclick="openModal('Tico', 'Um cãozinho alegre e cheio de energia, resgatado na Zona Sul.')">Ver Dados</button>
                </div>
            </div>

            <div class="pet-card" data-type="gato">
                <span class="pet-tag">Gato</span>
                <img src="https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=500" class="pet-img" alt="Aurora">
                <div class="pet-info">
                    <h3>Aurora</h3>
                    <p><i class="fas fa-venus-mars"></i> Fêmea | <i class="fas fa-cat"></i> Filhote</p>
                    <button class="btn-cta" style="margin-top:15px; width:100%" onclick="openModal('Aurora', 'Dócil e ronronante, adora um colo e sachê de salmão.')">Ver Dados</button>
                </div>
            </div>
            <div class="pets-grid" id="petsContainer">
            <div class="pet-card" data-type="cachorro">
                <span class="pet-tag">Cachorro</span>
                <img src="" class="pet-img" alt="Apollo">
                <div class="pet-info">
                    <h3>Apollo</h3>
                    <p><i class="fas fa-venus-mars"></i> Macho | <i class="fas fa-dog"></i> Porte Grande</p>
                    <button class="btn-cta" style="margin-top:15px; width:100%" onclick="openModal('Apollo', 'Valente, forte e sempre em alerta, Apollo é ex-cão do Batalhão de Ações Especiais da Polícia, e hoje procura um novo lar para curtir sua aposentadoria.')">Ver Dados</button>
                </div>
            </div>
        </div>
    </section>

    <section id="rotina" class="section-padding" style="background: #fdf2e9;">
        <h2 style="margin-bottom: 50px;">Nossa Rotina de Excelência</h2>
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
    </section>

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
                <h3 style="color: var(--primary); margin-bottom: 20px;">Abraço Animal</h3>
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
                <div style="display: flex; gap: 15px; font-size: 1.5rem; margin-top: 15px;">
                    <i class="fab fa-instagram"></i>
                    <i class="fab fa-facebook"></i>
                    <i class="fab fa-mail"></i>
                    <i class="fab fa-tiktok"></i>
                </div>
            </div>
        </div>
        <div style="text-align: center; margin-top: 50px; opacity: 0.6; font-size: 0.8rem;">
            CNPJ: 12.345.657/8910-11 | &copy; Abraço Animal 2026 | Todos os direitos reservados 
        </div>
    </footer>

    <script>
        // Mudança inteligente do estilo do Menu ao rolar a página
        window.addEventListener('scroll', function() {
            const nav = document.getElementById('navbar');
            if (window.scrollY > 50) {
                nav.classList.add('scrolled');
            } else {
                nav.classList.remove('scrolled');
            }
        });

        // Filtro de Animais
        function filterPets(type) {
            const cards = document.querySelectorAll('.pet-card');
            const btns = document.querySelectorAll('.filter-btn');
            
            btns.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

            cards.forEach(card => {
                if (type === 'todos' || card.getAttribute('data-type') === type) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        }

        // Sistema de Modal
        function openModal(name, desc) {
            document.getElementById('modalTitle').innerText = name;
            document.getElementById('modalDesc').innerText = desc;
            document.getElementById('petModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('petModal').style.display = 'none';
        }

        // Animações de Entrada (ScrollReveal)
        ScrollReveal().reveal('.reveal', { 
            delay: 200, 
            distance: '50px', 
            origin: 'bottom', 
            interval: 200 
        });

        ScrollReveal().reveal('.pet-card', { 
            delay: 300, 
            interval: 100,
            scale: 0.9
        });
    </script>
</body>
</html>
