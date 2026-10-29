<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Classics - Archivo Musical Histórico 60's, 70's, 80's y 90's</title>

  <!-- Google Fonts for Retro Aesthetics -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Pixelify+Sans:wght@500;700&family=VT323&display=swap" rel="stylesheet">

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            pixel: ['"Pixelify Sans"', 'cursive', 'sans-serif'],
            vt: ['"VT323"', 'monospace'],
            sans: ['"Inter"', 'sans-serif'],
          },
          colors: {
            retroBg: '#704646',
            retroGrupos: '#331C17',
            retroCantantes: '#47160E',
            retroAccent: '#7A2D1F',
            retroCream: '#F0E6D2',
            retroGold: '#D9A094',
            retroCardBg: '#3B2424',
          }
        }
      }
    }
  </script>

  <style>
    /* Global Styles & Scanline Effect */
    body {
      background-color: #704646;
      color: #F0E6D2;
      background-image: 
        linear-gradient(rgba(0,0,0,0.18) 1px, transparent 1px), 
        linear-gradient(90deg, rgba(0,0,0,0.18) 1px, transparent 1px);
      background-size: 28px 28px;
    }

    /* Custom Animations */
    @keyframes spin-slow {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    .animate-spin-slow {
      animation: spin-slow 3s linear infinite;
    }

    .playing .vinyl-disc {
      animation-play-state: running;
    }

    .paused .vinyl-disc {
      animation-play-state: paused;
    }

    /* Retro Box Shadow Effect */
    .fanzine-shadow {
      box-shadow: 8px 8px 0px #000000;
    }
    
    .poster-shadow {
      box-shadow: 10px 10px 0px #000000;
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #25100d;
    }
    ::-webkit-scrollbar-thumb {
      background: #7A2D1F;
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #D9A094;
    }
  </style>
</head>
<body class="min-h-screen antialiased flex flex-col items-center py-0 px-0 sm:px-4">

  <!-- Main Container -->
  <div class="w-full max-w-6xl bg-[#0f0707]/90 min-h-screen border-x-0 sm:border-x-2 border-black/80 shadow-2xl flex flex-col">

    <!-- Top Banner -->
    <div class="bg-gradient-to-r from-black via-[#331C17] to-black border-b-4 border-black py-5 px-4 text-center">
      <h2 class="font-pixel text-2xl sm:text-4xl text-retroGold tracking-wider uppercase mb-1 drop-shadow-md">
        ♫ Archivo Musical Histórico y Fanzine ♫
      </h2>
      <p class="font-sans text-xs sm:text-sm text-[#c4b5a5] tracking-widest uppercase">
        El templo definitivo del rock, el pop y los vinilos de las décadas 60s, 70s, 80s y 90s
      </p>
    </div>

    <!-- Header Section -->
    <header class="text-center py-8 px-4 bg-retroBg border-b-4 border-black">
      <span class="inline-block bg-black text-retroCream font-pixel px-3 py-1 text-sm rounded-sm mb-3 tracking-widest border border-retroGold/30">
        ★ 1960s - 1990s VINYL VAULT ★
      </span>
      <h1 class="font-pixel text-5xl sm:text-7xl font-bold text-black tracking-widest uppercase my-1 drop-shadow-lg">
        Classics
      </h1>
      <p class="font-bold text-black/90 text-sm sm:text-base uppercase tracking-widest">
        Colección Fanzine Interactiva
      </p>
    </header>

    <!-- Navigation Bar -->
    <nav class="sticky top-0 z-50 bg-black border-b-2 border-gray-800 flex justify-center gap-3 sm:gap-6 p-3">
      <button id="nav-vault-btn" onclick="switchView('vault')" class="px-4 py-2 font-pixel text-base sm:text-xl text-retroCream border border-gray-600 rounded hover:bg-retroCream hover:text-black transition duration-150 active">
        Vault General
      </button>
      <button id="nav-fanzine-btn" onclick="switchView('grupos')" class="px-4 py-2 font-pixel text-base sm:text-xl text-retroCream border border-gray-600 rounded hover:bg-retroCream hover:text-black transition duration-150">
        Catálogo Fanzine
      </button>
    </nav>

    <!-- MAIN CONTENT AREA -->
    <main class="flex-grow">

      <!-- 1. VAULT / CATALOG SECTION -->
      <section id="sec-vault" class="p-4 sm:p-8 bg-retroBg">
        <div class="max-w-4xl mx-auto mb-6">
          <h2 class="font-pixel text-3xl sm:text-4xl text-black font-bold mb-2">Explora Las Leyendas</h2>
          <p class="text-black font-semibold text-sm sm:text-base">
            Selecciona cualquier artista o banda para abrir su expediente histórico completo con biografías, comentarios e iframes musicales interactivos de Spotify.
          </p>
        </div>

        <!-- Filter & Search Bar -->
        <div class="bg-[#25100d] border-2 border-retroAccent p-4 rounded-lg mb-8 flex flex-col md:flex-row justify-between items-center gap-4">
          <div class="flex items-center gap-2 text-retroCream font-pixel text-lg">
            <span>⭐ Ordenar por:</span>
          </div>

          <div class="flex flex-wrap gap-2">
            <button id="sort-pop" onclick="sortDatabase('popularidad')" class="bg-retroAccent text-retroCream border border-retroGold px-3 py-1.5 font-pixel text-sm rounded hover:bg-retroGold hover:text-black transition">
              Popularidad
            </button>
            <button id="sort-year" onclick="sortDatabase('fecha')" class="bg-retroAccent text-retroCream border border-retroGold px-3 py-1.5 font-pixel text-sm rounded hover:bg-retroGold hover:text-black transition">
              Año (Cronológico)
            </button>
            <button id="sort-alpha" onclick="sortDatabase('alfabetico')" class="bg-retroAccent text-retroCream border border-retroGold px-3 py-1.5 font-pixel text-sm rounded hover:bg-retroGold hover:text-black transition">
              Alfabético
            </button>
          </div>

          <!-- Quick Search -->
          <div class="w-full md:w-auto">
            <input type="text" id="searchInput" oninput="filterSearch()" placeholder="Buscar artista..." class="w-full bg-[#120604] border border-retroAccent text-retroCream px-3 py-1.5 text-sm rounded focus:outline-none focus:border-retroGold">
          </div>
        </div>

        <!-- Grid Container -->
        <div id="vault-grid-container" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
          <!-- Dynamically Generated Cards -->
        </div>
      </section>

      <!-- 2. FANZINE / BAND DETAIL SECTION -->
      <section id="sec-grupos" class="hidden p-4 sm:p-8 bg-retroGrupos">
        <button onclick="switchView('vault')" class="bg-black text-retroCream border border-retroAccent px-4 py-2 font-pixel text-lg mb-6 hover:bg-retroAccent transition inline-block rounded-sm">
          ← Volver al Vault General
        </button>

        <!-- Fanzine Paper Card Container -->
        <div id="fanzine-content" class="bg-[#EAE1D0] text-gray-900 p-6 sm:p-10 border-4 border-black fanzine-shadow grid grid-cols-1 lg:grid-cols-3 gap-8">
          <!-- Dynamically populated -->
        </div>
      </section>

      <!-- 3. MEMBER POSTER / DOSSIER SECTION -->
      <section id="sec-integrante" class="hidden p-4 sm:p-8 bg-retroCantantes">
        <button id="btn-back-to-group" onclick="returnToGroup()" class="bg-black text-retroCream border border-retroAccent px-4 py-2 font-pixel text-lg mb-6 hover:bg-retroAccent transition inline-block rounded-sm">
          ← Volver al Grupo
        </button>

        <div id="poster-content" class="max-w-4xl mx-auto bg-[#120806] border-4 border-retroAccent p-6 sm:p-10 poster-shadow grid grid-cols-1 md:grid-cols-3 gap-8 text-retroCream">
          <!-- Dynamically populated -->
        </div>
      </section>

      <!-- 4. GLOBAL COMMUNITY & SPOTIFY PLAYLIST SECTION -->
      <section class="bg-[#261310] border-t-4 border-black p-6 sm:p-12 text-center">
        <h2 class="font-pixel text-3xl sm:text-5xl text-retroCream mb-3">Comunidad & Mixtape 80s</h2>
        <p class="max-w-2xl mx-auto text-[#c4b5a5] text-sm sm:text-base mb-8">
          Deja tu firma en el libro de visitas público y escucha la playlist en vivo recomendada.
        </p>

        <!-- Guestbook Box -->
        <div class="max-w-2xl mx-auto bg-[#1b0d0a] border-2 border-retroCantantes p-6 rounded-lg text-left mb-10">
          <h3 class="font-pixel text-2xl text-retroCream mb-4 text-center">Libro de Visitas Global</h3>
          
          <form onsubmit="addGlobalComment(event)" class="flex flex-col gap-3 mb-6">
            <input type="text" id="nombreGlobal" placeholder="Tu nombre o apodo..." required class="bg-[#110705] border border-retroAccent text-retroCream p-2.5 rounded text-sm focus:outline-none focus:border-retroGold">
            <textarea id="textoGlobal" rows="2" placeholder="Escribe tu mensaje fanzine..." required class="bg-[#110705] border border-retroAccent text-retroCream p-2.5 rounded text-sm focus:outline-none focus:border-retroGold"></textarea>
            <button type="submit" class="bg-retroAccent text-retroCream font-pixel text-lg py-2 rounded hover:bg-retroGold hover:text-black transition">
              Firmar Libro
            </button>
          </form>

          <div id="listaGlobal" class="flex flex-col gap-3 max-h-60 overflow-y-auto pr-2">
            <div class="bg-[#120806] border-l-4 border-retroAccent p-3 rounded">
              <div class="font-bold text-retroGold text-xs">Arthur P.</div>
              <div class="text-sm text-gray-300">¡Increíble estética ochentera y vinilos inolvidables! Gran archivo.</div>
            </div>
            <div class="bg-[#120806] border-l-4 border-retroAccent p-3 rounded">
              <div class="font-bold text-retroGold text-xs">Beatlemana77</div>
              <div class="text-sm text-gray-300">Excelente compilación de clásicos de los 60s y 70s.</div>
            </div>
          </div>
        </div>

        <!-- Global Spotify Playlist Container -->
        <div class="max-w-2xl mx-auto rounded-xl overflow-hidden border-2 border-retroGold/30 shadow-2xl">
          <iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/playlist/2fqFCun1xIQd4phZ6fptoA?utm_source=generator&si=0c780ed35c9e49ed" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
        </div>
      </section>

    </main>

    <!-- Footer -->
    <footer class="bg-black border-t border-gray-800 py-6 text-center text-xs text-gray-500 font-pixel">
      <p>CLASSICS FANZINE &copy; ARCHIVO MUSICAL HISTÓRICO — DÉCADAS 60s 70s 80s 90s</p>
    </footer>

  </div>

  <!-- JavaScript Codebase -->
  <script>
    // Main Music Database
    const baseDatos = [
      {
        id: "michaeljackson",
        nombre: "Michael Jackson",
        tipo: "solista",
        popularidad: 101,
        anio: 1964,
        fecha: "Activo desde: 1964 - 2009",
        coverImage: "https://i.pinimg.com/736x/a6/45/32/a645328975ae9c2d5530124d7faba71e.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/5BKKy9fIJL5uM9fz1SnqyP?utm_source=generator&si=1754f117d7244d3a" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Chicago",
        descripcionLarga: "Michael Jackson, indiscutiblemente coronado como el 'Rey del Pop', revolucionó para siempre la industria de la música, el baile y los videos musicales. Tras debutar siendo un niño prodigio en The Jackson 5, su carrera en solitario alcanzó cotas históricas insuperables con obras maestras absolutas de la producción discográfica como 'Off the Wall', 'Thriller' (el álbum más vendido de todos los tiempos en todo el planeta) y 'Bad'. Con éxitos inmortales que definieron a toda una era como 'Billie Jean', 'Beat It', 'Smooth Criminal', 'Thriller' y grandes joyas póstumas como 'Chicago', su genio artístico, su estilo vocal inconfundible y sus innovadores movimientos de baile perfeccionaron los estándares globales del espectáculo y el entretenimiento moderno.",
        comentarios: [{ autor: "Moonwalker", texto: "¡El Rey del Pop indiscutible de todos los tiempos!" }],
        miembros: [
          { id: "mj-solo", nombre: "Michael Jackson (Solista)", rol: "Vocalista, Compositor y Bailarín", foto: "https://i.pinimg.com/736x/a6/45/32/a645328975ae9c2d5530124d7faba71e.jpg", cancionNombre: "Chicago", historia: "Con su técnica vocal inconfundible, sus icónicos guantes de lentejuelas y pasos de baile revolucionarios como el 'Moonwalk', Michael Jackson redefinió por completo el concepto de la interpretación escénica global.", comentarios: [{ autor: "KingOfPop", texto: "¡Inigualable en el escenario y en el estudio!" }] }
        ]
      },
      {
        id: "elvispresley",
        nombre: "Elvis Presley",
        tipo: "solista",
        popularidad: 100,
        anio: 1954,
        fecha: "Activo desde: 1954 - 1977",
        coverImage: "https://i.pinimg.com/736x/b6/13/47/b61347d2dad8271b19478345fe600dcf.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/452KBpASS5lZLeJWX9Ixub?utm_source=generator&si=c4f676082b5d46aa" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Jailhouse Rock",
        descripcionLarga: "Elvis Presley, universalmente conocido como 'El Rey del Rock and Roll', es la figura fundacional más importante y trascendental de la música popular contemporánea. Surgido a mediados de los años cincuenta en Memphis, Tennessee, Elvis fusionó la música country con el rhythm and blues afroamericano, desatando una auténtica revolución cultural y juvenil en todo el mundo. Con una voz barítona magnética, una presencia escénica provocativa y arrolladora, y una ristra interminable de éxitos legendarios como 'Hound Dog', 'Jailhouse Rock', 'Suspicious Minds', 'Can't Help Falling in Love' y 'Heartbreak Hotel', se convirtió en el primer gran ícono global de la cultura de masas y el entretenimiento moderno.",
        comentarios: [{ autor: "TupeloFan", texto: "¡El rey que abrió las puertas a todo el rock!" }],
        miembros: [
          { id: "elvis-solo", nombre: "Elvis Presley (Solista)", rol: "Vocalista Principal e Icono Cultural", foto: "https://i.pinimg.com/736x/19/30/15/193015ec53004299e4790da50aec637b.jpg", cancionNombre: "Jailhouse Rock", historia: "Elvis transformó la estética y la actitud de la juventud mundial, convirtiéndose en el artista solista más vendido de la historia del rock.", comentarios: [{ autor: "RockabillyKing", texto: "¡Su voz y su estilo son inmortales!" }] }
        ]
      },
      {
        id: "beatles",
        nombre: "The Beatles",
        tipo: "banda",
        popularidad: 99,
        anio: 1960,
        fecha: "Fundación: 1960, Liverpool, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/a6/82/bb/a682bb8ca33e09b24f84ffb791463123.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/1eT2CjXwFXNx6oY5ydvzKU?utm_source=generator&si=926262002de2496e" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Ob-La-Di, Ob-La-Da",
        descripcionLarga: "The Beatles se consolidó como el fenómeno musical y cultural más colosal de la música popular del siglo XX. Surgidos en los clubes subterráneos de Liverpool y Hamburgo a principios de los sesenta bajo la tutela inicial de Brian Epstein y la genial producción de George Martin, el cuarteto redefinió por completo las estructuras del Pop y el Rock. Su impacto mundial dejó álbumes fundamentales que marcaron la historia como 'Rubber Soul', 'Revolver', 'Sgt. Pepper's Lonely Hearts Club Band' y 'Abbey Road', acumulando éxitos históricos e inmortales como 'Hey Jude', 'Yesterday', 'Let It Be' y 'Come Together'.",
        comentarios: [{ autor: "TamoPaul", texto: "¡El mejor grupo de todos los tiempos sin discusión!" }],
        miembros: [
          { id: "lennon", nombre: "John Lennon", rol: "Vocalista y Guitarrista Rítmico", foto: "https://i.pinimg.com/736x/18/0e/dc/180edccc35f09953ed2ebd8038b4ec12.jpg", cancionNombre: "Woman", historia: "John Lennon fue el cofundador, líder incisivo y alma creativa, poética y contestataria de The Beatles, además de un icono pacifista mundial.", comentarios: [{ autor: "Yoko ntfan", texto: "m agrada" }] },
          { id: "mccartney", nombre: "Paul McCartney", rol: "Bajista y Vocalista Principal", foto: "https://i.pinimg.com/736x/f1/88/12/f18812c806ca464416468a9e9c771e4f.jpg", cancionNombre: "Live and Let Die", historia: "Sir James Paul McCartney es reconocido universalmente como uno de los compositores, bajistas y melodistas más exitosos y prolíficos de la historia de la música.", comentarios: [{ autor: "Jude", texto: "¡Genio absoluto del bajo y las melodías!" }] },
          { id: "harrison", nombre: "George Harrison", rol: "Guitarrista Líder y Compositor", foto: "https://i.pinimg.com/736x/56/39/28/5639283971ac53ddb43296bb9ec87df9.jpg", cancionNombre: "My Sweet Lord", historia: "Conocido como 'el Beatle silencioso', aportó una tremenda profundidad espiritual a la banda e introdujo de manera magistral los sonidos de la India a través del sitar.", comentarios: [{ autor: "Ravi", texto: "Su música espiritual vive por siempre en el corazón." }] },
          { id: "ringo", nombre: "Ringo Starr", rol: "Baterista y Percusionista", foto: "https://i.pinimg.com/736x/93/c6/5f/93c65f4babd59258b7225aceb1f465b3.jpg", cancionNombre: "Have You Seen My Baby", historia: "Ringo Starr aportó un groove de batería sólido, innovador y sumamente influyente, además de un carisma entrañable que completó la magia del cuarteto.", comentarios: [{ autor: "Peace & Love", texto: "¡El baterista con más carisma y buen corazón!" }] }
        ]
      },
      {
        id: "queen",
        nombre: "Queen",
        tipo: "banda",
        popularidad: 98,
        anio: 1970,
        fecha: "Fundación: 1970, Londres, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/43/4d/a2/434da29b83014d327e97cbacc4d36714.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/4vMukJaEhIUqH2xxCKrtKN?utm_source=generator&si=f999a4d627c14819" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Under Pressure",
        descripcionLarga: "Queen se erige por derecho propio como una de las agrupaciones de Rock más teatrales, ambiciosas, suntuosas y aclamadas de toda la historia musical. Fusionando el Hard Rock tradicional con complejas armonías vocales de corte operístico, suntuosos arreglos corales y una energía arrolladora, la banda liderada por Freddie Mercury creó obras maestras absolutas como 'A Night at the Opera' y canciones inmortales como 'Bohemian Rhapsody', 'We Will Rock You', 'Don't Stop Me Now', 'Another One Bites the Dust' y 'Radio Ga Ga'. Sus legendarias actuaciones en directo son consideradas cátedras absolutas de cómo dominar estadios enteros.",
        comentarios: [{ autor: "BohemianFan", texto: "¡Una fuerza operística e instrumental incomparable!" }],
        miembros: [
          { id: "freddie", nombre: "Freddie Mercury", rol: "Vocalista Principal y Pianista", foto: "https://i.pinimg.com/736x/35/14/a2/3514a20f30fb4d559fa4e8adc7dbe264.jpg", cancionNombre: "Under Pressure", historia: "Freddie Mercury fue un showman legendario e inigualable, dotado de un registro vocal de cuatro octavas y una capacidad histriónica y magnética única sobre los escenarios.", comentarios: [{ autor: "Stadium Guy", texto: "El mejor vocalista y frontman de toda la historia del rock." }] },
          { id: "brian", nombre: "Brian May", rol: "Guitarrista Líder y Astrofísico", foto: "https://i.pinimg.com/736x/bf/0a/d6/bf0ad6e5abdac495e2689303113a3cdc.jpg", cancionNombre: "Tie Your Mother Down", historia: "Legendario guitarrista creador de la famosa guitarra casera 'Red Special', responsable de los muros de guitarras armónicas y riffs icónicos de Queen.", comentarios: [{ autor: "AstroRock", texto: "¡Riffs y solos de guitarra absolutamente inolvidables!" }] }
        ]
      },
      {
        id: "rollingstones",
        nombre: "The Rolling Stones",
        tipo: "banda",
        popularidad: 97,
        anio: 1962,
        fecha: "Fundación: 1962, Londres, Inglaterra",
        coverImage: "https://i.pinimg.com/1200x/aa/d0/50/aad0509a7cdf76091ddee26f9dc95b59.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/73SPjNZV2wVy8imEmckGYw?utm_source=generator&si=f33baa3ee4cf412b" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Paint It Black",
        descripcionLarga: "The Rolling Stones es la encarnación viva y definitiva del espíritu canalla, rebelde, crudo y bluesero del Rock and Roll. Formada en Londres en 1962, la mítica banda conocida como 'Su Majestad Satánica' ha dominado los escenarios mundiales durante más de seis décadas gracias a la dupla creativa imparable y legendaria formada por Mick Jagger y Keith Richards. Con álbumes de estudio magistrales que definieron el sonido de una época como 'Let It Bleed', 'Exile on Main St.' y 'Sticky Fingers', y canciones inmortales como '(I Can't Get No) Satisfaction', 'Paint It Black', 'Sympathy for the Devil' y 'Jumpin' Jack Flash', se mantienen firmemente como el grupo de rock en activo más longevo y respetado de la historia.",
        comentarios: [{ autor: "RockeroViejitaEscuela", texto: "¡La banda de rock and roll más grande y peligrosa del mundo!" }],
        miembros: [
          { id: "mick-jagger", nombre: "Mick Jagger", rol: "Vocalista Principal y Líder", foto: "https://i.pinimg.com/736x/6d/05/8d/6d058ddf153fef33abe9155b30aa4391.jpg", cancionNombre: "Paint It Black", historia: "Mick Jagger redefinió para siempre el arquetipo del frontman con su carisma magnético, su energía escénica inagotable y su inconfundible voz llena de blues.", comentarios: [{ autor: "JaggerFan", texto: "¡Una energía física y vocal única en todo el planeta!" }] },
          { id: "keith-richards", nombre: "Keith Richards", rol: "Guitarrista Líder y Compositor", foto: "https://i.pinimg.com/736x/a4/b4/ff/a4b4ffbd22cc0d7d225d6f577ffed374.jpg", cancionNombre: "Paint It Black", historia: "Keith Richards es el alma rítmica y el cerebro de los riffs maestros de los Stones, inmortalizado por su estilo de vida indomable y su genial toque guitarrístico.", comentarios: [{ autor: "RiffKing", texto: "hermoso" }] }
        ]
      },
      {
        id: "ledzeppelin",
        nombre: "Led Zeppelin",
        tipo: "banda",
        popularidad: 96,
        anio: 1968,
        fecha: "Fundación: 1968, Londres, Inglaterra",
        coverImage: "https://i.pinimg.com/1200x/2f/d9/15/2fd9157609d54295f5ec382a5f3d1bbd.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/0DANcJuMamcL9NyYkEWWTq?utm_source=generator&si=114bc0d0754b4fc3" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Stairway to Heaven",
        descripcionLarga: "Led Zeppelin es ampliamente considerada la banda de Hard Rock y Heavy Metal más grande, pesada e influyente de todos los tiempos. Integrada por cuatro monstruos musicales, fusionaron el blues tradicional británico con la psicodelia y la potencia instrumental descomunal. Creadores de monumentos musicales como 'Stairway to Heaven', 'Kashmir', 'Whole Lotta Love' y 'Immigrant Song', sentaron los cimientos definitivos de la música pesada moderna a través de discos conceptuales y directos titánicos.",
        comentarios: [{ autor: "ZeppelinFan", texto: "¡Stairway to Heaven es la absoluta cumbre del rock!" }],
        miembros: [
          { id: "robert-plant", nombre: "Robert Plant", rol: "Vocalista Principal", foto: "https://i.pinimg.com/736x/90/74/1f/90741ff30c4e1b47dce578e94997847c.jpg", cancionNombre: "Stairway to Heaven", historia: "Conocido como 'The Golden God', su poderosa e imponente voz de altas tesituras definió el sonido vocal del hard rock de los años setenta.", comentarios: [{ autor: "GoldenGod", texto: "DE LOS MEJORES" }] },
          { id: "jimmy-page", nombre: "Jimmy Page", rol: "Guitarrista Líder y Productor", foto: "https://i.pinimg.com/1200x/fd/27/15/fd27159c2ec470a46662d9b8bbaf124a.jpg", cancionNombre: "Stairway to Heaven", historia: "Arquitecto sonoro y mago de las seis cuerdas, responsable de algunos de los riffs más pesados y memorables de la historia musical.", comentarios: [{ autor: "RiffMaster", texto: "amo el solo de stairway to heaven!" }] }
        ]
      },
      {
        id: "acdc",
        nombre: "AC/DC",
        tipo: "banda",
        popularidad: 95,
        anio: 1973,
        fecha: "Fundación: 1973, Sídney, Australia",
        coverImage: "https://i.pinimg.com/1200x/20/64/cc/2064ccef5ddcea9d5f8059bda2d11f79.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/08mG3Y1vljYA6bvDt4Wqkj?utm_source=generator&si=4e3a7a7f0a014fbb" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Back in Black",
        descripcionLarga: "AC/DC es una de las instituciones más potentes, directas e inquebrantables del Hard Rock mundial. Fundada en Australia por los hermanos Malcolm y Angus Young, la banda construyó un imperio sonoro basado en el rock and roll puro, sin artificios y de altísimo voltaje. Con álbumes consagratorios como 'Back in Black' (el tercer disco más vendido de la historia) y 'Highway to Hell', e himnos de estadios colosales como 'Thunderstruck', 'You Shook Me All Night Long' y 'Hells Bells', siguen llenando estadios en todo el mundo.",
        comentarios: [{ autor: "Rockero80", texto: "¡El riff de Back in Black es una biblia del rock!" }],
        miembros: [
          { id: "brian-johnson", nombre: "Brian Johnson", rol: "Vocalista Principal", foto: "https://i.pinimg.com/736x/8e/ed/b6/8eedb6e3435796bfc8fb83f79646f3f3.jpg", cancionNombre: "Back in Black", historia: "Con su inseparable gorra plana y su voz sumamente rasposa y enérgica, relevó con enorme éxito tras la tragedia de Bon Scott en el álbum Back in Black.", comentarios: [{ autor: "FanACDC", texto: "¡Una voz y una actitud única en el mundo!" }] },
          { id: "angus-young", nombre: "Angus Young", rol: "Guitarrista Líder", foto: "https://i.pinimg.com/736x/38/f0/27/38f027a27dc9ef7695cd4c19354ac33f.jpg", cancionNombre: "Back in Black", historia: "El rey indiscutible de los directos con su característico uniforme escolar, sus solos frenéticos y su energía inagotable con su guitarra Gibson SG.", comentarios: [{ autor: "GuitarHero", texto: "¡El guitarrista más eléctrico y dinámico que existe!" }] }
        ]
      },
      {
        id: "beegees",
        nombre: "Bee Gees",
        tipo: "banda",
        popularidad: 94,
        anio: 1958,
        fecha: "Fundación: 1958, Redcliffe, Australia",
        coverImage: "https://i.pinimg.com/736x/94/9b/8a/949b8a0ebcb1f56160f6bf5688fd3f31.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/5ubvP9oKmxLUVq506fgLhk?utm_source=generator&si=d4aacbeebe5f4f71" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Stayin' Alive",
        descripcionLarga: "Bee Gees, formado por los hermanos Barry, Robin y Maurice Gibb, es uno de los grupos vocales más exitosos, influyentes y comerciales de todos los tiempos. Aunque comenzaron en los años sesenta como una aclamada banda de pop melódico y folk barroco, se convirtieron en los indiscutibles reyes globales de la era disco a finales de los setenta gracias a la banda sonora de la película 'Saturday Night Fever' ('Fiebre de Sábado por la Noche'). Con sus legendarias e inconfundibles armonías vocales en falsete y éxitos colosales como 'Stayin' Alive', 'Night Fever', 'How Deep Is Your Love' y 'Tragedy', vendieron más de 220 millones de discos, redefiniendo la música de baile mundial.",
        comentarios: [{ autor: "DiscoKing", texto: "¡Los reyes absolutos de la música disco y las armonías!" }],
        miembros: [
          { id: "barry-gibb", nombre: "Barry Gibb", rol: "Vocalista en Falsete y Guitarrista", foto: "https://i.pinimg.com/736x/9a/e1/95/9ae195308415d0639e9746393346c98e.jpg", cancionNombre: "Stayin' Alive", historia: "Líder vocal y compositor principal de los Bee Gees, famoso por su icónico y potente falsete que definió el sonido de la cultura disco de los setenta.", comentarios: [{ autor: "FalsettoMaster", texto: "¡Una voz y talento compositivo legendario!" }] }
        ]
      },
      {
        id: "eltonjohn",
        nombre: "Elton John",
        tipo: "solista",
        popularidad: 92,
        anio: 1967,
        fecha: "Activo desde: 1967",
        coverImage: "https://i.pinimg.com/736x/e6/60/6f/e6606f1acc634e10710d6b608a0903fe.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/6BQpa5YSEHdoHEy2uiRHyN?utm_source=generator&si=d241f0bb1d3e4ade" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Rocket Man",
        descripcionLarga: "Sir Elton John es uno de los artistas solistas, compositores y pianistas más exitosos, extravagantes y queridos de la historia de la música universal. En una legendaria e inseparable asociación compositiva con el letrista Bernie Taupin, ha creado un repertorio de baladas y temas pop-rock insuperables que incluye obras maestras como 'Rocket Man', 'Your Song', 'Tiny Dancer', 'Bennie and the Jets', 'I'm Still Standing' y 'Candle in the Wind'. Con sus deslumbrantes atuendos escénicos y su virtuosismo al piano, ha vendido cientos de millones de discos en todo el mundo.",
        comentarios: [{ autor: "PianoMan", texto: "¡El rey indiscutible del piano y la melodía pop!" }],
        miembros: [
          { id: "elton-solo", nombre: "Elton John (Solista)", rol: "Vocalista y Pianista Virtuoso", foto: "https://i.pinimg.com/736x/02/51/11/02511113ff26e4834d6e5336f179a933.jpg", cancionNombre: "Rocket Man", historia: "Con una carrera estelar de más de cinco décadas, Elton John ha combinado a la perfección el virtuosismo clásico del piano con el pop y el rock de estadios.", comentarios: [{ autor: "RocketFan", texto: "¡Un showman y músico absolutamente legendario!" }] }
        ]
      },
      {
        id: "fleetwoodmac",
        nombre: "Fleetwood Mac",
        tipo: "banda",
        popularidad: 91,
        anio: 1967,
        fecha: "Fundación: 1967, Londres, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/da/d1/58/dad158dbd05ed3aa6946f2ab5e6a5df1.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/0ofHAoxe9vBkTCp2UQIavz?utm_source=generator&si=694615536c7e4809" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Dreams",
        descripcionLarga: "Fleetwood Mac pasó de ser una respetada banda de blues británico en los sesenta a convertirse en un titán absoluto del pop-rock melódico mundial en los setenta, tras la incorporación de la dupla estadounidense formada por Stevie Nicks y Lindsey Buckingham. Su álbum de 1977, 'Rumours', grabado en medio de intensos y cruzados dramas amorosos y personales entre sus miembros, se convirtió en uno de los discos más vendidos, aclamados y perfectos de la historia de la música, conteniendo himnos eternos como 'Dreams', 'Go Your Own Way', 'The Chain', 'You Make Loving Fun' y 'Gypsy'.",
        comentarios: [{ autor: "RumoursFan", texto: "¡Magia musical y emocional pura en cada canción!" }],
        miembros: [
          { id: "stevie-nicks", nombre: "Stevie Nicks", rol: "Vocalista y Compositora", foto: "https://i.pinimg.com/736x/52/09/0c/52090c91b30c60ef82c9878878931317.jpg", cancionNombre: "Dreams", historia: "Conocida como 'la reina del rock and roll', su estética mística, su voz ronca inconfundible y su talento lírico transformaron a Fleetwood Mac en leyenda.", comentarios: [{ autor: "WhiteDove", texto: "¡Una bruja mágica y compositora sin igual!" }] }
        ]
      },
      {
        id: "bobdylan",
        nombre: "Bob Dylan",
        tipo: "solista",
        popularidad: 89,
        anio: 1961,
        fecha: "Activo desde: 1959",
        coverImage: "https://i.pinimg.com/1200x/00/67/8b/00678b54e6ad9f97775a8664dbe4969d.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/3AhXZa8sUQht0UEdBJgpGc?utm_source=generator&si=f871179c2a6045f4" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Like a Rolling Stone",
        descripcionLarga: "Bob Dylan es una de las figuras intelectuales y musicales más influyentes de la cultura popular de los siglos XX y XXI. Poeta, cantautor, pintor y voz incombustible de toda una generación de protesta social en los sesenta, Dylan revolucionó tanto la música folk acústica como el rock eléctrico al dotar a las letras de las canciones de una profundidad poética, literaria y crítica sin precedentes en la historia. Es autor de himnos generacionales inmortales como 'Like a Rolling Stone', 'Blowin' in the Wind', 'Knockin' on Heaven's Door' y 'The Times They Are a-Changin'', siendo galardonado de forma histórica con el Premio Nobel de Literatura.",
        comentarios: [{ autor: "FolkPoet", texto: "¡El boticario y poeta definitivo!" }],
        miembros: [
          { id: "bobdylan-solo", nombre: "Bob Dylan (Solista)", rol: "Cantautor y Poeta", foto: "https://i.pinimg.com/736x/aa/61/21/aa6121c55c4cbd1ce3613f520b244a57.jpg", cancionNombre: "Like a Rolling Stone", historia: "Su pluma afilada, su armónica y su estilo interpretativo cambiaron para siempre la forma en que la humanidad entendía el poder narrativo de una canción popular.", comentarios: [{ autor: "NobelMusic", texto: "¡Un genio literario y musical que marcó la historia!" }] }
        ]
      },
      {
        id: "thedoors",
        nombre: "The Doors",
        tipo: "banda",
        popularidad: 88,
        anio: 1965,
        fecha: "Fundación: 1965, Los Ángeles, California",
        coverImage: "https://i.pinimg.com/736x/e3/61/d3/e361d3e288c4c3ab114ce343ca243764.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/1Q5kgpp4pmyGqPwNBzkSrw?utm_source=generator&si=2ea91018b3864a0e" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Roadhouse Blues",
        descripcionLarga: "The Doors combinó de manera brillante la poesía oscura, provocativa y chamánica de Jim Morrison con un sonido de rock psicodélico, blues y jazz hipnótico sustentado por el inconfundible órgano de Ray Manzarek y la guitarra de Robby Krieger. Sin utilizar bajo eléctrico en sus directos, la banda angelina dejó un catálogo de canciones atemporales y místicas que incluye joyas absolutas como 'Light My Fire', 'Riders on the Storm', 'Break On Through (To the Other Side)', 'The End' y 'Roadhouse Blues'.",
        comentarios: [{ autor: "RiderOnTheStorm", texto: "¡Pura psicodelia mística y poética de los sesenta!" }],
        miembros: [
          { id: "morrison", nombre: "Jim Morrison", rol: "Poeta y Vocalista Principal", foto: "https://i.pinimg.com/736x/45/33/c2/4533c264eb6625da4e526e4247dd8782.jpg", cancionNombre: "Roadhouse Blues", historia: "Conocido como 'El Rey Lagarto', Jim Morrison poseía una intensidad volcánica, intelectual y carismática sin igual sobre el escenario.", comentarios: [{ autor: "Mr Mojo Risin", texto: "¡El poeta rebelde y chamán del rock vive por siempre!" }] }
        ]
      },
      {
        id: "journey",
        nombre: "Journey",
        tipo: "banda",
        popularidad: 87,
        anio: 1973,
        fecha: "Fundación: 1973, San Francisco, California",
        coverImage: "https://i.pinimg.com/736x/43/5d/ac/435dac8c565dd94b43a7c4a0a513f69b.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/77NNZQSqzLNqh2A9JhLRkg?utm_source=generator&si=3e65864e7a674115" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Don't Stop Believin'",
        descripcionLarga: "Journey es el estandarte supremo, comercial y virtuoso del Arena Rock norteamericano de finales de los setenta y los ochenta. Surgidos en San Francisco bajo la batuta del ex-guitarrista de Santana Neal Schon, alcanzaron la gloria absoluta tras la llegada del vocalista Steve Perry. Su repertorio incluye algunos de los himnos melódicos más coreados y reproducidos de la historia del rock, como 'Don't Stop Believin'', 'Separate Ways (Worlds Apart)', 'Open Arms', 'Faithfully' y 'Any Way You Want It'.",
        comentarios: [{ autor: "ArenaRock", texto: "¡Himnos motivacionales de estadio insuperables!" }],
        miembros: [
          { id: "steve-perry", nombre: "Steve Perry", rol: "Vocalista Principal", foto: "https://i.pinimg.com/736x/fa/d6/24/fad6242cec8ee966192bc1721109a17b.jpg", cancionNombre: "Don't Stop Believin'", historia: "Apodado con total justicia 'The Voice', su registro vocal de tenor claro, emotivo y cristalino definió por completo el sonido melódico del rock de estadios.", comentarios: [{ autor: "TheVoice", texto: "¡Una voz privileged que te hace llorar de emoción!" }] }
        ]
      },
      {
        id: "beachboys",
        nombre: "The Beach Boys",
        tipo: "banda",
        popularidad: 86,
        anio: 1961,
        fecha: "Fundación: 1961, Hawthorne, California",
        coverImage: "https://i.pinimg.com/1200x/0e/37/d8/0e37d8093bdea69c4795f926ebea6b77.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/6VojZJpMyuKClbwyilWlQj?utm_source=generator&si=f51d7136f26c498d" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Wouldn't It Be Nice",
        descripcionLarga: "The Beach Boys revolucionaron para siempre la música Pop de los sesenta al fusionar la temática alegre de la cultura del surf y los automóviles californianos con unas armonías vocales celestiales, complejas y sofisticadas. Bajo la genial y atormentada dirección compositiva de Brian Wilson, el grupo dio un salto vanguardista monumental con la creación del álbum maestro 'Pet Sounds' (1966) y la sinfonía pop de bolsillo 'Good Vibrations', consolidándose como una de las agrupaciones más influyentes y creativas de la historia.",
        comentarios: [{ autor: "SurferGirl", texto: "¡Las armonías vocales más bellas y celestiales del pop!" }],
        miembros: [
          { id: "brian-wilson", nombre: "Brian Wilson", rol: "Compositor, Pianista y Productor", foto: "https://i.pinimg.com/1200x/9c/91/5a/9c915af47af5baaf01950fbeea05e51f.jpg", cancionNombre: "Wouldn't It Be Nice", historia: "Genio absoluto de la composición y los arreglos de estudio, considerado uno de los cerebros musicales más dotados del siglo XX.", comentarios: [{ autor: "PetSoundsFan", texto: "¡Un genio musical absoluto e inimitable!" }] }
        ]
      },
      {
        id: "carlossantana",
        nombre: "Carlos Santana",
        tipo: "solista",
        popularidad: 86,
        anio: 1966,
        fecha: "Activo desde: 1966",
        coverImage: "https://i.pinimg.com/736x/70/e3/f3/70e3f30fec464dfd01fded48f5f9305b.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/3XKIUb7HzIF1Vu9usunMzc?utm_source=generator&si=c195b59dc5784ce4" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Maria Maria",
        descripcionLarga: "Carlos Santana es un legendario guitarrista mexicano-estadounidense pionero absoluto en fusionar el rock psicodélico de los sesenta con los ritmos latinos, la salsa, el jazz y el afrobeat. Desde su histórica, abrasadora y explosiva aparición en el festival de Woodstock en 1969 al frente de su banda homónima, su guitarra eléctrica de tono sustain cálido, espiritual y melódico ha cautivado al planeta entero. Su carrera cuenta con discos legendarios y clásicos inmortales como 'Black Magic Woman', 'Oye Como Va', 'Evil Ways' y el multipremiado álbum 'Supernatural' (1999) con el éxito global 'Smooth'.",
        comentarios: [{ autor: "LatinRock", texto: "¡El sonido de su guitarra tiene alma, fuego y espíritu latino!" }],
        miembros: [
          { id: "santana-solo", nombre: "Carlos Santana (Solista)", rol: "Guitarrista Líder y Compositor", foto: "https://i.pinimg.com/736x/48/1e/26/481e26216a6216b19c64543cd0bec30f.jpg", cancionNombre: "Black Magic Woman", historia: "Con su estilo espiritual, emotivo y su icónica guitarra Paul Reed Smith, Santana logró conectar de manera magistral las raíces latinas con el rock universal.", comentarios: [{ autor: "WoodstockFan", texto: "¡Magia pura y espiritualidad en cada nota que toca!" }] }
        ]
      },
      {
        id: "bowie",
        nombre: "David Bowie",
        tipo: "solista",
        popularidad: 85,
        anio: 1962,
        fecha: "Activo desde: 1962 - 2016",
        coverImage: "https://i.pinimg.com/736x/b6/0e/a4/b60ea4557ceff2028ee8ada768af1f14.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/0pQskrTITgmCMyr85tb9qq?utm_source=generator&si=0bd558c1c677459e" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Starman",
        descripcionLarga: "El gran camaleón de la música, David Bowie, transformó y adelantó las fronteras de la cultura Pop moderna gracias a sus constantes reinvenciones estéticas, conceptuales y musicales a lo largo de cinco décadas. Desde su alter ego espacial 'Ziggy Stardust' hasta su etapa de soul plástico y su trilogía electrónica de Berlín, Bowie dejó un catálogo discográfico inmortal encabezado por obras maestras como 'Space Oddity', 'Starman', 'Heroes', 'Let's Dance', 'Life on Mars?' y 'Rebel Rebel', influyendo profundamente en el arte, la moda y el rock mundial.",
        comentarios: [{ autor: "Ziggy Stardust", texto: "¡El duque blanco delgado y el artista más vanguardista de la historia!" }],
        miembros: [
          { id: "bowie-solo", nombre: "David Bowie (Solista)", rol: "Vocalista, Productor y Artista Visual", foto: "https://i.pinimg.com/736x/f3/cf/7b/f3cf7b18428067aa3251f7490967cf10.jpg", cancionNombre: "Starman", historia: "Reinventor constante de su imagen musical y teatral, Bowie fusionó la alta cultura con el rock para convertirse en un mito intergaláctico.", comentarios: [{ autor: "Starman Fan", texto: "¡Absolutamente único, vanguardista e irrepetible!" }] }
        ]
      },
      {
        id: "dio",
        nombre: "DIO",
        tipo: "banda",
        popularidad: 85,
        anio: 1982,
        fecha: "Fundación: 1982, Los Ángeles, California",
        coverImage: "https://i.pinimg.com/736x/41/75/59/41755925163a07fff5709f0b992a76f7.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/4wBxOGbbVIVkCJGCM5zwVo?utm_source=generator&si=8734b71c68474634" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Holy Diver",
        descripcionLarga: "Dio fue una influyente banda de Heavy Metal estadounidense fundada en 1982 por el legendario e irremplazable vocalista Ronnie James Dio, tras su paso estelar por bandas capitales como Rainbow y Black Sabbath. Con un sonido pesado, épico, oscuro y lleno de fantasía medieval y mitológica, la banda debutó con el aclamado álbum clásico 'Holy Diver' (1983), que incluyó himnos inmortales del género como la canción homónima y 'Rainbow in the Dark', además de discos fundamentales como 'The Last in Line'. Ronnie James Dio es también mundialmente famoso por popularizar el famoso gesto de la 'mano cornuta' en el mundo del rock.",
        comentarios: [{ autor: "MetalHead80", texto: "¡La voz más poderosa, limpia y épica del heavy metal!" }],
        miembros: [
          { id: "ronnie-james-dio", nombre: "Ronnie James Dio", rol: "Vocalista Principal y Líder", foto: "https://i.pinimg.com/736x/bb/ea/4d/bbea4d59b6bcc4d95421f65a3d8a1a1e.jpg", cancionNombre: "Holy Diver", historia: "Dueño de una potencia vocal operística, limpia y desgarradora inigualable, Dio definió la temática lírica de fantasía dentro del heavy metal tradicional.", comentarios: [{ autor: "SignOfTheHorns", texto: "¡El padrino supremo del metal!" }] }
        ]
      },
      {
        id: "toto",
        nombre: "TOTO",
        tipo: "banda",
        popularidad: 84,
        anio: 1977,
        fecha: "Fundación: 1977, Los Ángeles, California",
        coverImage: "https://i.pinimg.com/1200x/c2/bf/6f/c2bf6f6960866bd0565b79598d163e77.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/2374M0fQpWi3dLnB54qaLX?utm_source=generator&si=788089b72e9f41a2" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Africa",
        descripcionLarga: "Integrada por los músicos de sesión más talentosos, técnicos y solicitados de la industria de Los Ángeles, TOTO dominó la escena Pop-Rock mundial de finales de los setenta y ochenta gracias a su impecable virtuosismo instrumental, que combinaba pop, rock, jazz y funk con arreglos sofisticados. Ganadores de múltiples premios Grammy con su legendario álbum 'Toto IV', son creadores universales del éxito global 'Africa', así como de otros inmensos clásicos del formato radiofónico como 'Hold the Line' y 'Rosanna'.",
        comentarios: [{ autor: "SoftRock80", texto: "¡Africa es una obra maestra absoluta de la producción musical!" }],
        miembros: [
          { id: "steve-lukather", nombre: "Steve Lukather", rol: "Guitarrista Líder y Vocalista", foto: "https://i.pinimg.com/736x/e4/bb/6f/e4bb6fdd98dd194369f1d353ac2dabca.jpg", cancionNombre: "Africa", historia: "Virtuoso indiscutible de la guitarra, guitarrista de sesión de miles de discos y pilar técnico y creativo de TOTO.", comentarios: [{ autor: "GuitarMaster", texto: "¡Un músico con un nivel técnico y un gusto exquisito!" }] }
        ]
      },
      {
        id: "thecars",
        nombre: "The Cars",
        tipo: "banda",
        popularidad: 83,
        anio: 1976,
        fecha: "Fundación: 1976, Boston, Massachusetts",
        coverImage: "https://i.pinimg.com/1200x/89/c4/a2/89c4a2861c9aef77d6d60fe8ddd2dba5.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/5xLfQuX5YAfog2JgPz0dpA?utm_source=generator&si=3a00859a52e14062" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Moving in Stereo",
        descripcionLarga: "Pioneros absolutos del New Wave y el Pop-Rock estadounidense de finales de los setenta y ochenta, The Cars combinaron de manera magistral texturas robóticas de sintetizadores futuristas con guitarras afiladas de rock clásico y estribillos sumamente pegadizos. Liderados por la distintiva voz y pluma de Ric Ocasek, conquistaron las listas mundiales con álbumes icónicos y canciones insuperables como 'Drive', 'Just What I Needed', 'My Best Friend's Girl', 'Shake It Up' y 'Moving in Stereo'.",
        comentarios: [{ autor: "NewWaveFan", texto: "¡Sonido futurista, ganchos pop y rock clásico perfectos!" }],
        miembros: [
          { id: "ocasek", nombre: "Ric Ocasek", rol: "Vocalista y Compositor Principal", foto: "https://i.pinimg.com/1200x/bf/9d/a8/bf9da879197c5aedba954e65ea8e820a.jpg", cancionNombre: "Moving in Stereo", historia: "Cerebro creativo, productor y compositor de los ganchos melódicos más inteligentes del movimiento new wave.", comentarios: [{ autor: "StereoGuy", texto: "¡Un genio del estudio y del pop sintético!" }] }
        ]
      },
      {
        id: "bonjovi",
        nombre: "Bon Jovi",
        tipo: "banda",
        popularidad: 82,
        anio: 1983,
        fecha: "Fundación: 1983, Sayreville, Nueva Jersey",
        coverImage: "https://i.pinimg.com/736x/2c/8d/f3/2c8df3872b13479d85e1df6887c328e0.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/37ZJ0p5Jm13JPevGcx4SkF?utm_source=generator&si=fc4b7b8f78e64c44" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Livin' on a Prayer",
        descripcionLarga: "Bon Jovi definió de forma rotunda el sonido masivo del Arena Rock, el Hard Rock melódico y el Glam Metal comercial de mediados y finales de los ochenta. Originarios de Nueva Jersey y liderados por el carismático Jon Bon Jovi y el guitarrista Richie Sambora, alcanzaron la estratosfera comercial con el histórico álbum 'Slippery When Wet' (1986). Son creadores de himnos generacionales e inmortales de estadios como 'Livin' on a Prayer', 'You Give Love a Bad Name', 'Wanted Dead or Alive' y el gran éxito de los dos mil 'It's My Life'.",
        comentarios: [{ autor: "JerseyGirl", texto: "¡Himnos de estadio totales para cantar a pleno pulmón!" }],
        miembros: [
          { id: "jon-bonjovi", nombre: "Jon Bon Jovi", rol: "Vocalista Principal y Fundador", foto: "https://i.pinimg.com/736x/59/ed/02/59ed02084ade9ffe6f7146c439accd05.jpg", cancionNombre: "Livin' on a Prayer", historia: "Motor creativo, rostro icónico y líder carismático de una de las bandas de rock más taquilleras y longevas de la historia.", comentarios: [{ autor: "It's My Life", texto: "¡Una energía inagotable y un carisma de estrella total!" }] }
        ]
      },
      {
        id: "tearsforfears",
        nombre: "Tears for Fears",
        tipo: "banda",
        popularidad: 81,
        anio: 1981,
        fecha: "Fundación: 1981, Bath, Inglaterra",
        coverImage: "https://i.pinimg.com/1200x/7f/ff/b2/7fffb276aea5756061f06169261e6aff.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/4RvWPyQ5RL0ao9LPZeSouE?utm_source=generator&si=59057c13bafa443e" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Everybody Wants to Rule the World",
        descripcionLarga: "Íconos absolutos del Synth-Pop inteligente, el rock alternativo y la nueva ola británica de los ochenta, Tears for Fears destacó enormemente por fusionar producciones atmosféricas de sintetizadores con profundas letras de corte psicológico inspiradas en la terapia primal de Arthur Janov. Formada por Roland Orzabal y Curt Smith, la banda alcanzó la cima mundial con su obra maestra conceptual 'Songs from the Big Chair' (1985), regalando a la historia himnos generacionales tan rotundos como 'Everybody Wants to Rule the World', 'Shout', 'Head over Heels' y 'Mad World'.",
        comentarios: [{ autor: "SynthWave80", texto: "¡El synth-pop más inteligente, profundo y elegante de los ochenta!" }],
        miembros: [
          { id: "roland-orzabal", nombre: "Roland Orzabal", rol: "Vocalista Principal y Guitarrista", foto: "https://i.pinimg.com/736x/80/a3/bb/80a3bbea380216015180626c42eced26.jpg", cancionNombre: "Everybody Wants to Rule the World", historia: "Cerebro musical principal, compositor y voz de la mayoría de los grandes éxitos conceptuales y melódicos del dúo británico.", comentarios: [{ autor: "OrzabalFan", texto: "¡Un genio compositivo y vocal extraordinario!" }] }
        ]
      },
      {
        id: "billyidol",
        nombre: "Billy Idol",
        tipo: "solista",
        popularidad: 81,
        anio: 1981,
        fecha: "Activo desde: 1976",
        coverImage: "https://i.pinimg.com/736x/f0/50/8b/f0508be29c7a840abc28d8b8b4dab585.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/0pUVeEgZuNyFzIMKp67RbS?utm_source=generator&si=64676ba0e47d4b0a" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "eyes without a face",
        descripcionLarga: "Billy Idol se erigió como la gran superestrella masculina del cruce entre el Punk Rock primigenio y el brillante Pop-Rock de los sintetizadores de los años ochenta. Tras iniciar su carrera en la banda punk Generation X, Idol dio el salto a Estados Unidos para iniciar una exitosa carrera en solitario caracterizada por su icónica estética de cuero negro, su rubio platinado despeinado, su famosa mueca de labios y el demoledor toque de guitarra de Steve Stevens. Es autor de auténticos himnos generacionales del rock ochentero como 'Rebel Yell', 'White Wedding', 'Eyes Without a Face' y 'Cradle of Love'.",
        comentarios: [{ autor: "PunkRock80", texto: "¡La actitud punk perfecta combinada con ganchos pop inigualables!" }],
        miembros: [
          { id: "billyidol-solo", nombre: "Billy Idol (Solista)", rol: "Vocalista y Compositor", foto: "https://i.pinimg.com/736x/59/15/14/591514a8a944d06c714d65beebb8e8cd.jpg", cancionNombre: "Rebel Yell", historia: "Con su carisma rebelde y su voz rasposa inconfundible, Billy Idol personificó la chulería y la energía eléctrica del rock ochentero.", comentarios: [{ autor: "RebelYellFan", texto: "¡Una estrella del rock con una energía inigualable!" }] }
        ]
      },
      {
        id: "buckley",
        nombre: "Jeff Buckley",
        tipo: "solista",
        popularidad: 80,
        anio: 1990,
        fecha: "Activo desde: 1990 - 1997",
        coverImage: "https://i.pinimg.com/736x/01/04/d2/0104d28e4b1a5a680597aeb04d3da792.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/6Jv7kjGkhY2fT4yuBF3aTz?utm_source=generator&si=137b1859f5f44fd8" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Lover, You Should've Come Over",
        descripcionLarga: "Con una voz etérea, conmovedora y de un rango vocal de cuatro octavas, Jeff Buckley cautivó por completo al mundo de la música alternativa con la publicación de su único álbum de estudio en vida, 'Grace' (1994). A pesar de su trágica y prematura muerte en 1997, Buckley dejó un legado poético, guitarrístico y desgarrador encabezado por su magistral, celestial y definitiva versión del tema 'Hallelujah' de Leonard Cohen, así como joyas de la composición moderna como 'Lover, You Should've Come Over' y 'Last Goodbye'.",
        comentarios: [{ autor: "GraceFan", texto: "Su voz celestial y desgarradora te llega directamente al alma." }],
        miembros: [
          { id: "jeff-solo", nombre: "Jeff Buckley (Solista)", rol: "Vocalista Principal y Guitarrista", foto: "https://i.pinimg.com/736x/da/0a/77/da0a77638e45f673d7afacb4353fa4b5.jpg", cancionNombre: "Lover, You Should've Come Over", historia: "Su único y singular estilo de ejecución a la guitarra eléctrica y su sensibilidad interpretativa sellaron su estatus de mito eterno.", comentarios: [{ autor: "Hallelujah", texto: "Una obra maestra absoluta de belleza inalcanzable." }] }
        ]
      },
      {
        id: "boston",
        nombre: "Boston",
        tipo: "banda",
        popularidad: 79,
        anio: 1975,
        fecha: "Fundación: 1975, Boston, Massachusetts",
        coverImage: "https://i.pinimg.com/736x/80/f7/87/80f7872d910d896a3e038cf06d05baf0.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/1QEEqeFIZktqIpPI4jSVSF?utm_source=generator&si=47ecdbed09f44d6f" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "More Than a Feeling",
        descripcionLarga: "Fundada y orquestada casi en su totalidad por el brillante ingeniero de sonido y graduado del MIT Tom Scholz, la banda Boston revolucionó por completo los estándares del Rock de los setenta gracias a un sonido de guitarras hiperarmonizadas, prístinas y producidas con una perfección milimétrica en su estudio casero. Su álbum debut homónimo de 1976 se convirtió en uno de los mayores éxitos de ventas de todos los tiempos en la historia de la música, albergando himnos atemporales del rock clásico como 'More Than a Feeling', 'Peace of Mind' y 'Foreplay / Long Time'.",
        comentarios: [{ autor: "ClassicRock", texto: "¡El muro de guitarras armónicas más perfecto de la historia del rock!" }],
        miembros: [
          { id: "tom-scholz", nombre: "Tom Scholz", rol: "Guitarrista, Compositor y Productor", foto: "https://i.pinimg.com/736x/10/6f/04/106f0465ac3c4b0c387343ffe74fad0d.jpg", cancionNombre: "More Than a Feeling", historia: "Visionario absoluto de la ingeniería de sonido y multiinstrumentista que cambió los métodos de grabación discográfica del rock clásico.", comentarios: [{ autor: "ScholzGenius", texto: "¡Un genio absoluto de la física del sonido y la guitarra!" }] }
        ]
      },
      {
        id: "valens",
        nombre: "Ritchie Valens",
        tipo: "solista",
        popularidad: 78,
        anio: 1958,
        fecha: "Activo desde: 1958 - 1959",
        coverImage: "https://i.pinimg.com/736x/8f/ee/ca/8feecac6474f1cc67f61c76b80f1b97b.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/5jjrPdeClupQkNkGR1sth7?utm_source=generator&si=738f1b6fa5474e99" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Oh, Donna",
        descripcionLarga: "Ritchie Valens es recordado de forma imborrable como un auténtico pionero del Rock and Roll y el indiscutible precursor del rock chicano y latino en la industria musical de los Estados Unidos. A pesar de que su fulgurante carrera musical duró apenas ocho meses debido a su trágica muerte en el fatídico accidente aéreo conocido como 'El día que murió la música' en 1959 a la temprana edad de 17 años, Valens logró inmortalizar clásicos absolutos como su electrizante versión rockera del son jarocho tradicional 'La Bamba', así como las hermosas baladas románticas 'Oh, Donna' y 'Come On, Let's Go', abriendo las puertas del mercado anglosajón a la cultura hispana.",
        comentarios: [{ autor: "LaBambaFan", texto: "¡Un talento precoz y luminoso que transformó la historia del rock!" }],
        miembros: [
          { id: "valens-solo", nombre: "Ritchie Valens (Solista)", rol: "Cantautor y Guitarrista Pionero", foto: "https://i.pinimg.com/736x/d0/f8/ee/d0f8eea2af2c0ad8c239107f32c67e81.jpg", cancionNombre: "Oh, Donna", historia: "Conquistó las listas de éxitos internacionales siendo un adolescente, convirtiéndose en el primer gran héroe musical de la comunidad latina en EE. UU.", comentarios: [{ autor: "ChicanoRock", texto: "¡Su legado juvenil brilla e inspira por siempre!" }] }
        ]
      },
      {
        id: "spandauballet",
        nombre: "Spandau Ballet",
        tipo: "banda",
        popularidad: 77,
        anio: 1979,
        fecha: "Fundación: 1979, Londres, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/71/35/ca/7135cacb16610a5830736cecdf11a92a.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/10I09MLZCY4pK37XxAfkw0?utm_source=generator&si=23f57288db624fbf" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "True",
        descripcionLarga: "Spandau Ballet fue uno de los grupos abanderados más lujosos, elegantes e influyentes del movimiento británico de los años ochenta conocido como los 'New Romantics' (Nuevos Románticos). Surgidos en los clubes nocturnos de Londres, el quinteto combinó sofisticados arreglos de pop electrónico, funk bailable y baladas orquestales de altísima factura estética. Su consagración mundial llegó con el álbum 'True' (1983), cuyo tema homónimo se convirtió en uno de los mayores y más hermosos éxitos románticos de la década, complementado por otros grandes hits internacionales como 'Gold' y 'Through the Barricades'.",
        comentarios: [{ autor: "NewRomantic80", texto: "¡Elegancia total, sintetizadores y romanticismo de los ochenta!" }],
        miembros: [
          { id: "tony-hadley", nombre: "Tony Hadley", rol: "Vocalista Principal", foto: "https://i.pinimg.com/736x/4d/e6/ef/4de6ef6c1d9c989de77c751fd980ee85.jpg", cancionNombre: "True", historia: "Dueño de una voz de barítono potente, soulera y sumamente distinguida, Hadley personificó la opulencia y el estilo vocal de los nuevos románticos.", comentarios: [{ autor: "GoldFan", texto: "¡Una voz dorada y majestuosa!" }] }
        ]
      },
      {
        id: "whitestripes",
        nombre: "The White Stripes",
        tipo: "banda",
        popularidad: 75,
        anio: 1997,
        fecha: "Fundación: 1997, Detroit, Míchigan",
        coverImage: "https://i.pinimg.com/1200x/7b/b2/55/7bb25519b2142fd2a88120e231718add.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/3dPQuX8Gs42Y7b454ybpMR?utm_source=generator&si=ca42ddfff2494282" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Seven Nation Army",
        descripcionLarga: "Dúo fundamental y capital en la masiva revitalización mundial del Garage Rock y el Blues-Rock alternativo a principios de los años dos mil. Formado en Detroit por Jack White y Meg White, el grupo destacó tanto por su estética visual minimalista y estricta basada únicamente en los colores rojo, blanco y negro, como por su sonido crudo, visceral y desprovisto de bajo eléctrico. Su obra cumbre, 'Elephant' (2003), incluyó el legendario himno intergeneracional de estadios 'Seven Nation Army', además de joyas como 'Fell in Love with a Girl' y 'The Hardest Button to Button'.",
        comentarios: [{ autor: "GarageFan", texto: "¡Energía analógica pura, minimalismo y un riff legendario!" }],
        miembros: [
          { id: "jack-white", nombre: "Jack White", rol: "Vocalista, Guitarrista y Productor", foto: "https://i.pinimg.com/1200x/ff/77/4c/ff774c3a5c0e266d99e74ddf73fa36c2.jpg", cancionNombre: "Seven Nation Army", historia: "Innovador incansable de la guitarra analógica y defensor acérrimo del equipo vintage de vinilo y sonido valvular.", comentarios: [{ autor: "VinylLovers", texto: "¡Un genio moderno del rock y la guitarra analógica!" }] }
        ]
      },
      {
        id: "dexys",
        nombre: "Dexys Midnight Runners",
        tipo: "banda",
        popularidad: 72,
        anio: 1978,
        fecha: "Fundación: 1978, Birmingham, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/3f/80/6e/3f806e2ed6e4a86d4f53c3fc1566b7d9.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/3MrWxJaD2AT0W9DjWF64Vm?utm_source=generator&si=882fb2ca8c6f4a79" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Come On Eileen",
        descripcionLarga: "Banda británica célebre y singular por su explosiva, festiva e innovadora mezcla de Soul clásico de Motown, Pop orquestal y violines e instrumentos del Folk celta tradicional. Liderados por el exigente e impredecible Kevin Rowland, alcanzaron la gloria comercial internacional absoluta en 1982 con la publicación del inmortal y alegre himno generacional 'Come On Eileen', perteneciente a su aclamado álbum 'Too-Rye-Ay', además de dejar otros grandes temas de culto como 'Geno'.",
        comentarios: [{ autor: "80sKid", texto: "¡Es imposible escuchar Come On Eileen y no ponerse a bailar!" }],
        miembros: [
          { id: "kevin-rowland", nombre: "Kevin Rowland", rol: "Vocalista Principal y Fundador", foto: "https://i.pinimg.com/736x/c7/5b/04/c75b04784682a4497d17a97d4be09126.jpg", cancionNombre: "Come On Eileen", historia: "Líder perfeccionista, apasionado y sumamente enérgico del grupo, famoso por sus particulares cambios estéticos a lo largo de las décadas.", comentarios: [{ autor: "SoulMan", texto: "¡Una voz llena de alma, desgarro y pasión celta!" }] }
        ]
      },
      {
        id: "gunsnroses",
        nombre: "Guns N’ Roses",
        tipo: "banda",
        popularidad: 90,
        anio: 1985,
        fecha: "Fundación: 1985, Los Ángeles, California",
        coverImage: "https://i.pinimg.com/1200x/7b/0c/bf/7b0cbf6e4c716e125f1fadc2d81ebec5.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/7snQQk1zcKl8gZ92AnueZW?utm_source=generator&si=338e771df1ab42bd" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Sweet Child O’ Mine",
        descripcionLarga: "Guns N’ Roses irrumpió en los años ochenta con actitud callejera y salvaje con Appetite for Destruction, el álbum debut más vendido de la historia, con éxitos como Sweet Child O’ Mine, Welcome to the Jungle y November Rain.",
        comentarios: [{ autor: "ParadiseCity", texto: "¡Puro peligro y actitud callejera de los ochenta!" }],
        miembros: [
          { 
            id: "axl-rose", 
            nombre: "Axl Rose", 
            rol: "Vocalista Principal", 
            foto: "https://i.pinimg.com/736x/d6/e5/5b/d6e55bf8e079b23f15080d939bd2fe92.jpg", 
            cancionNombre: "November Rain", 
            historia: "Vocalista de rango descomunal y autor intelectual de complejas obras maestras como November Rain.", 
            comentarios: [{ autor: "Gunner", texto: "¡Una voz inconfundible!" }] 
          },
          { 
            id: "slash", 
            nombre: "Slash", 
            rol: "Guitarrista Líder", 
            foto: "https://i.pinimg.com/736x/ca/ea/43/caea43c13bc44a63f644718b6df82564.jpg", 
            cancionNombre: "Sweet Child O’ Mine", 
            historia: "El icono de la guitarra con sombrero de copa y solos llenos de blues.", 
            comentarios: [{ autor: "GibsonSG", texto: "¡El rey de la guitarra Les Paul!" }] 
          }
        ]
      },
      {
        id: "plainwhitets",
        nombre: "Plain White T's",
        tipo: "banda",
        popularidad: 70,
        anio: 1997,
        fecha: "Fundación: 1997, Chicago, Illinois",
        coverImage: "https://i.pinimg.com/1200x/72/74/fa/7274fa5fd7a6e44db6c848a6e7159b71.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/4RCWB3V8V0dignt99LZ8vH?utm_source=generator&si=86e91a97fd7742a8" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Hey There Delilah",
        descripcionLarga: "Banda norteamericana de Rock Alternativo, Pop Rock y Pop Punk originaria de Chicago, inmortalizada gracias a su balada acústica Hey There Delilah.",
        comentarios: [{ autor: "AcousticLover", texto: "Un clásico acústico inolvidable." }],
        miembros: [
          { id: "tom-higgenson", nombre: "Tom Higgenson", rol: "Vocalista Principal", foto: "https://i.pinimg.com/736x/7f/df/0c/7fdf0c481e3d55a8d68399c0449a8c23.jpg", cancionNombre: "Hey There Delilah", historia: "Compositor del éxito romántico que dio la vuelta al mundo.", comentarios: [] }
        ]
      },
      {
        id: "Duranduran",
        nombre: "Duran Duran",
        tipo: "banda",
        popularidad: 93,
        anio: 1978,
        fecha: "Fundación: 1978, Birmingham, Inglaterra",
        coverImage: "https://i.pinimg.com/736x/22/a1/cf/22a1cf9c6ad057b393ff26e9a18c9bf6.jpg",
        embedSoundCloud: `<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/1ff8lsrJ2kuZuofMw81EQo?utm_source=generator&si=52092f688a9e4853" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>`,
        cancionNombre: "Save a prayer",
        descripcionLarga: "Duran Duran se convirtió en la banda estandarte y más elegante del movimiento New Romantic y de la llamada Segunda Invasión Británica en MTV durante los años ochenta. Combinando sintetizadores pop pegadizos, elegantes ritmos de baile y videoclips icónicos filmados en exóticas locaciones, el grupo británico conquistó el planeta con éxitos legendarios como Hungry Like the Wolf, Rio, Ordinary World y Save a Prayer.",
        comentarios: [{ autor: "hola123", texto: "me encanta" }],
        miembros: [
          { id: "taylor", nombre: "John Taylor", rol: "Vocalista Principal y Guitarrista", foto: "https://i.pinimg.com/1200x/96/4d/e5/964de5f46f46efecd1fb04c5df69f962.jpg", cancionNombre: "save a prayer", historia: "Compositor principal y autor del famosísimo éxito de la banda.", comentarios: [{ autor: "hola123", texto: "amo esto" }] }
        ]
      }
    ];

    // State Variables
    let currentGroup = null;
    let filteredDatabase = [...baseDatos];

    // Initialize App
    window.onload = function() {
      sortDatabase('popularidad');
    };

    // Render Vault Catalog Grid
    function renderVaultGrid() {
      const container = document.getElementById('vault-grid-container');
      container.innerHTML = '';

      if (filteredDatabase.length === 0) {
        container.innerHTML = `
          <div class="col-span-full text-center py-12 text-retroCream font-pixel">
            <p class="text-2xl">No se encontraron artistas con ese criterio de búsqueda.</p>
          </div>
        `;
        return;
      }

      filteredDatabase.forEach(item => {
        const card = document.createElement('div');
        card.className = "bg-retroCardBg border-2 border-black rounded-lg overflow-hidden cursor-pointer hover:-translate-y-1 hover:shadow-xl transition duration-200 flex flex-col justify-between";
        card.onclick = () => openGroup(item.id);

        card.innerHTML = `
          <div>
            <div class="relative h-48 overflow-hidden bg-black">
              <img src="${item.coverImage}" alt="${item.nombre}" class="w-full h-full object-cover opacity-90 hover:scale-105 transition duration-300 onerror="this.src='https://placehold.co/400x300/3B2424/F0E6D2?text=${encodeURIComponent(item.nombre)}'">
              <span class="absolute top-2 right-2 bg-black/80 text-retroGold text-xs font-pixel px-2 py-1 rounded border border-retroGold/40">
                ⭐ ${item.popularidad} pts
              </span>
              <span class="absolute bottom-2 left-2 bg-retroAccent text-retroCream text-xs font-pixel px-2 py-0.5 rounded">
                ${item.anio}
              </span>
            </div>
            <div class="p-4">
              <h3 class="font-pixel text-xl sm:text-2xl text-retroCream mb-1 leading-tight">${item.nombre}</h3>
              <p class="text-xs text-retroGold font-semibold uppercase tracking-wider mb-2">
                ${item.tipo === 'banda' ? '✦ BANDA HISTÓRICA' : '✦ ARTISTA SOLISTA'}
              </p>
              <p class="text-xs text-gray-300 line-clamp-2">${item.descripcionLarga}</p>
            </div>
          </div>
          <div class="p-4 pt-0">
            <span class="block text-center font-pixel text-xs bg-black/60 text-retroCream py-1.5 rounded border border-retroAccent hover:bg-retroAccent transition">
              Abrir Expediente ➔
            </span>
          </div>
        `;
        container.appendChild(card);
      });
    }

    // Sort Handler
    function sortDatabase(mode) {
      document.querySelectorAll('#sort-pop, #sort-year, #sort-alpha').forEach(b => {
        b.classList.remove('bg-retroGold', 'text-black');
        b.classList.add('bg-retroAccent', 'text-retroCream');
      });

      if (mode === 'popularidad') {
        baseDatos.sort((a, b) => b.popularidad - a.popularidad);
        document.getElementById('sort-pop').classList.add('bg-retroGold', 'text-black');
      } else if (mode === 'fecha') {
        baseDatos.sort((a, b) => a.anio - b.anio);
        document.getElementById('sort-year').classList.add('bg-retroGold', 'text-black');
      } else if (mode === 'alfabetico') {
        baseDatos.sort((a, b) => a.nombre.localeCompare(b.nombre));
        document.getElementById('sort-alpha').classList.add('bg-retroGold', 'text-black');
      }
      
      filterSearch();
    }

    // Filter Search
    function filterSearch() {
      const query = document.getElementById('searchInput').value.toLowerCase().trim();
      filteredDatabase = baseDatos.filter(item => 
        item.nombre.toLowerCase().includes(query) || 
        item.cancionNombre.toLowerCase().includes(query) ||
        item.descripcionLarga.toLowerCase().includes(query)
      );
      renderVaultGrid();
    }

    // Navigation Switcher
    function switchView(viewName) {
      document.querySelectorAll('#sec-vault, #sec-grupos, #sec-integrante').forEach(sec => sec.classList.add('hidden'));
      document.querySelectorAll('#nav-vault-btn, #nav-fanzine-btn').forEach(btn => btn.classList.remove('bg-retroCream', 'text-black'));

      if (viewName === 'vault') {
        document.getElementById('sec-vault').classList.remove('hidden');
        document.getElementById('nav-vault-btn').classList.add('bg-retroCream', 'text-black');
        window.scrollTo({ top: 0, behavior: 'smooth' });
      } else if (viewName === 'grupos') {
        openGroup(currentGroup || baseDatos[0].id);
      }
    }

    // Open Fanzine Group Dossier
    function openGroup(id) {
      currentGroup = id;
      const index = baseDatos.findIndex(x => x.id === id);
      if (index === -1) return;
      const data = baseDatos[index];

      document.querySelectorAll('#sec-vault, #sec-grupos, #sec-integrante').forEach(sec => sec.classList.add('hidden'));
      document.getElementById('sec-grupos').classList.remove('hidden');
      document.getElementById('nav-fanzine-btn').classList.add('bg-retroCream', 'text-black');
      window.scrollTo({ top: 0, behavior: 'smooth' });

      const prevIndex = (index - 1 + baseDatos.length) % baseDatos.length;
      const nextIndex = (index + 1) % baseDatos.length;
      const prevGroup = baseDatos[prevIndex];
      const nextGroup = baseDatos[nextIndex];

      let miembrosHtml = '';
      data.miembros.forEach(m => {
        miembrosHtml += `
          <button onclick="openMember('${data.id}', '${m.id}')" class="bg-black text-retroCream hover:bg-retroAccent p-2.5 rounded text-left font-semibold text-xs sm:text-sm border border-black transition">
            👤 ${m.nombre} <span class="text-retroGold font-normal">(${m.rol})</span>
          </button>
        `;
      });

      let comentariosHtml = '';
      if (data.comentarios && data.comentarios.length > 0) {
        data.comentarios.forEach(c => {
          comentariosHtml += `
            <div class="bg-[#120806] border-l-4 border-retroAccent p-3 rounded">
              <div class="font-bold text-retroGold text-xs">${escapeHtml(c.autor)}</div>
              <div class="text-sm text-gray-200">${escapeHtml(c.texto)}</div>
            </div>
          `;
        });
      } else {
        comentariosHtml = `<p class="text-xs text-gray-400 italic">Sé el primero en dejar un comentario.</p>`;
      }

      const container = document.getElementById('fanzine-content');
      container.innerHTML = `
        <!-- Main Bio -->
        <div class="lg:col-span-2 flex flex-col justify-between">
          <div>
            <h2 class="font-pixel text-4xl sm:text-6xl text-black border-b-2 border-black pb-2 mb-3">${data.nombre}</h2>
            <p class="font-bold text-retroAccent text-sm uppercase tracking-widest mb-4">${data.fecha}</p>
            <div class="prose max-w-none text-gray-800 text-sm sm:text-base leading-relaxed text-justify mb-6">
              ${data.descripcionLarga}
            </div>
          </div>

          <!-- Members Box -->
          <div class="bg-[#dfd5c2] border-2 border-black p-4 rounded-md mt-4">
            <h3 class="font-pixel text-xl sm:text-2xl text-black mb-2">Integrantes Y Solistas Destacados:</h3>
            <p class="text-xs text-gray-700 mb-3">Haz clic en cualquier integrante para inspeccionar su póster y expediente individual:</p>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
              ${miembrosHtml}
            </div>
          </div>
        </div>

        <!-- Sidebar / Media Player -->
        <div class="flex flex-col gap-6">
          <div class="border-2 border-black p-2 bg-white rounded shadow">
            <img src="${data.coverImage}" alt="${data.nombre}" class="w-full h-64 sm:h-80 object-cover rounded" onerror="this.src='https://placehold.co/400x500/3B2424/F0E6D2?text=${encodeURIComponent(data.nombre)}'">
          </div>

          <!-- Spotify Player Embed -->
          <div class="bg-[#110705] border-2 border-black p-2 rounded-lg shadow">
            ${data.embedSoundCloud}
          </div>
        </div>

        <!-- Comments Section -->
        <div class="lg:col-span-3 bg-[#220e0b] text-retroCream border-2 border-retroAccent p-6 rounded-lg mt-4">
          <h4 class="font-pixel text-2xl text-retroCream mb-3">Comentarios sobre ${data.nombre}</h4>
          
          <form onsubmit="addArtistComment(event, '${data.id}')" class="flex flex-col sm:flex-row gap-3 mb-6">
            <input type="text" id="autor-${data.id}" placeholder="Tu nombre..." required class="bg-[#120604] border border-retroAccent text-retroCream p-2 rounded text-sm sm:w-1/3 focus:outline-none focus:border-retroGold">
            <input type="text" id="texto-${data.id}" placeholder="Escribe tu opinión..." required class="bg-[#120604] border border-retroAccent text-retroCream p-2 rounded text-sm flex-grow focus:outline-none focus:border-retroGold">
            <button type="submit" class="bg-retroAccent text-retroCream font-pixel text-base px-4 py-2 rounded hover:bg-retroGold hover:text-black transition">
              Comentar
            </button>
          </form>

          <div id="lista-comentarios-${data.id}" class="flex flex-col gap-3 max-h-48 overflow-y-auto pr-2">
            ${comentariosHtml}
          </div>
        </div>

        <!-- Pagination Controls -->
        <div class="lg:col-span-3 flex justify-between items-center gap-4 pt-4 border-t-2 border-dashed border-gray-800">
          <button onclick="openGroup('${prevGroup.id}')" class="bg-black text-retroCream border border-retroAccent px-4 py-2 font-pixel text-sm sm:text-base hover:bg-retroAccent transition rounded">
            ⬅ ${prevGroup.nombre}
          </button>
          <button onclick="openGroup('${nextGroup.id}')" class="bg-black text-retroCream border border-retroAccent px-4 py-2 font-pixel text-sm sm:text-base hover:bg-retroAccent transition rounded">
            ${nextGroup.nombre} ➡️
          </button>
        </div>
      `;
    }

    // Open Member Dossier
    function openMember(grupoId, miembroId) {
      const grupo = baseDatos.find(x => x.id === grupoId);
      if (!grupo) return;
      const miembro = grupo.miembros.find(m => m.id === miembroId);
      if (!miembro) return;

      document.querySelectorAll('#sec-vault, #sec-grupos, #sec-integrante').forEach(sec => sec.classList.add('hidden'));
      document.getElementById('sec-integrante').classList.remove('hidden');
      window.scrollTo({ top: 0, behavior: 'smooth' });

      let comentariosMiembroHtml = '';
      if (miembro.comentarios && miembro.comentarios.length > 0) {
        miembro.comentarios.forEach(c => {
          comentariosMiembroHtml += `
            <div class="bg-[#140705] border-l-4 border-retroAccent p-2.5 rounded">
              <div class="font-bold text-retroGold text-xs">${escapeHtml(c.autor)}</div>
              <div class="text-sm text-gray-300">${escapeHtml(c.texto)}</div>
            </div>
          `;
        });
      } else {
        comentariosMiembroHtml = `<p class="text-xs text-gray-400 italic">No hay notas registradas para este integrante.</p>`;
      }

      // Check if member has an iframe embed or fallback vinyl
      let memberPlayerHtml = '';
      if (miembro.embedSoundCloud) {
        memberPlayerHtml = `<div class="mt-4 rounded-lg overflow-hidden">${miembro.embedSoundCloud}</div>`;
      } else {
        memberPlayerHtml = `
          <div class="bg-[#22120F] border border-retroAccent p-4 rounded text-center mt-4">
            <p class="font-pixel text-retroGold text-lg mb-1">♫ CANCIÓN DESTACADA</p>
            <p class="text-xs text-gray-300">${miembro.cancionNombre || 'Tema Clásico'}</p>
          </div>
        `;
      }

      const posterContainer = document.getElementById('poster-content');
      posterContainer.innerHTML = `
        <div class="md:col-span-1">
          <img src="${miembro.foto}" alt="${miembro.nombre}" class="w-full h-80 object-cover border-2 border-retroAccent rounded shadow-md" onerror="this.src='https://placehold.co/400x500/3B2424/F0E6D2?text=${encodeURIComponent(miembro.nombre)}'">
          ${memberPlayerHtml}
        </div>

        <div class="md:col-span-2 flex flex-col justify-between">
          <div>
            <h2 class="font-pixel text-3xl sm:text-5xl text-retroCream mb-1">${miembro.nombre}</h2>
            <span class="text-retroGold font-bold text-xs uppercase tracking-widest block mb-4">
              ${miembro.rol} — (${grupo.nombre})
            </span>

            <div class="border-t border-retroAccent pt-3 mb-4">
              <h4 class="font-pixel text-xl text-retroGold mb-2">Trayectoria e Historia Personal</h4>
              <p class="text-sm text-gray-300 leading-relaxed text-justify">${miembro.historia}</p>
            </div>
          </div>

          <!-- Comments Section for Member -->
          <div class="bg-[#1b0a08] border border-retroAccent p-4 rounded mt-4">
            <h4 class="font-pixel text-lg text-retroCream mb-2">Notas sobre ${miembro.nombre}</h4>
            
            <form onsubmit="addMemberComment(event, '${grupo.id}', '${miembro.id}')" class="flex gap-2 mb-3">
              <input type="text" id="autor-m-${miembro.id}" placeholder="Tu nombre..." required class="bg-[#120604] border border-retroAccent text-retroCream p-1.5 text-xs rounded w-1/3 focus:outline-none">
              <input type="text" id="texto-m-${miembro.id}" placeholder="Nota..." required class="bg-[#120604] border border-retroAccent text-retroCream p-1.5 text-xs rounded flex-grow focus:outline-none">
              <button type="submit" class="bg-retroAccent text-retroCream font-pixel text-xs px-3 py-1 rounded hover:bg-retroGold hover:text-black transition">
                Guardar
              </button>
            </form>

            <div id="lista-comentarios-m-${miembro.id}" class="flex flex-col gap-2 max-h-36 overflow-y-auto pr-1">
              ${comentariosMiembroHtml}
            </div>
          </div>
        </div>
      `;
    }

    // Return to Active Group
    function returnToGroup() {
      if (currentGroup) {
        openGroup(currentGroup);
      } else {
        switchView('vault');
      }
    }

    // Add Comment Handlers
    function addArtistComment(e, artistaId) {
      e.preventDefault();
      const autor = document.getElementById(`autor-${artistaId}`).value.trim();
      const texto = document.getElementById(`texto-${artistaId}`).value.trim();
      if (!autor || !texto) return;

      const artista = baseDatos.find(x => x.id === artistaId);
      if (artista) {
        if (!artista.comentarios) artista.comentarios = [];
        artista.comentarios.unshift({ autor, texto });
        openGroup(artistaId);
      }
    }

    function addMemberComment(e, grupoId, miembroId) {
      e.preventDefault();
      const autor = document.getElementById(`autor-m-${miembroId}`).value.trim();
      const texto = document.getElementById(`texto-m-${miembroId}`).value.trim();
      if (!autor || !texto) return;

      const grupo = baseDatos.find(x => x.id === grupoId);
      if (grupo) {
        const miembro = grupo.miembros.find(m => m.id === miembroId);
        if (miembro) {
          if (!miembro.comentarios) miembro.comentarios = [];
          miembro.comentarios.unshift({ autor, texto });
          openMember(grupoId, miembroId);
        }
      }
    }

    function addGlobalComment(e) {
      e.preventDefault();
      const nombre = document.getElementById('nombreGlobal').value.trim();
      const texto = document.getElementById('textoGlobal').value.trim();
      if (!nombre || !texto) return;

      const list = document.getElementById('listaGlobal');
      const item = document.createElement('div');
      item.className = 'bg-[#120806] border-l-4 border-retroAccent p-3 rounded';
      item.innerHTML = `
        <div class="font-bold text-retroGold text-xs">${escapeHtml(nombre)}</div>
        <div class="text-sm text-gray-300">${escapeHtml(texto)}</div>
      `;
      list.prepend(item);

      document.getElementById('nombreGlobal').value = '';
      document.getElementById('textoGlobal').value = '';
    }

    // Escape HTML Helper
    function escapeHtml(text) {
      const map = { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#039;' };
      return text.replace(/[&<>"']/g, function(m) { return map[m]; });
    }
  </script>
</body>
</html>
