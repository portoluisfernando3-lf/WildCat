# WildCat
Oi
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wildcat</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, Helvetica, sans-serif;
    }body {
  background: #ffffff;
  color: #000000;
  min-height: 100vh;
}

.app {
  max-width: 520px;
  margin: 0 auto;
  min-height: 100vh;
  background: #ffffff;
  border-left: 1px solid #e5e5e5;
  border-right: 1px solid #e5e5e5;
}

header {
  position: sticky;
  top: 0;
  z-index: 10;
  background: #ffffff;
  border-bottom: 1px solid #e5e5e5;
  padding: 14px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-size: 28px;
  font-weight: 900;
  letter-spacing: -1px;
  color: #000000;
}

.logo span {
  color: #159947;
}

button {
  border: none;
  background: #159947;
  color: #ffffff;
  padding: 10px 14px;
  border-radius: 999px;
  font-weight: 700;
  cursor: pointer;
}

button:hover {
  filter: brightness(0.95);
}

.ghost-btn {
  background: #f1f1f1;
  color: #000000;
}

.screen {
  display: none;
  padding: 18px 16px 86px;
}

.screen.active {
  display: block;
}

.card {
  border: 1px solid #e5e5e5;
  border-radius: 18px;
  padding: 16px;
  margin-bottom: 16px;
  background: #ffffff;
}

.login-box {
  margin-top: 46px;
  text-align: center;
}

.login-box h1 {
  font-size: 38px;
  margin-bottom: 10px;
}

.login-box p {
  margin-bottom: 18px;
  color: #333333;
  line-height: 1.4;
}

input, textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #cccccc;
  border-radius: 12px;
  margin-bottom: 12px;
  color: #000000;
  background: #ffffff;
  font-size: 15px;
}

textarea {
  resize: vertical;
  min-height: 80px;
}

label {
  font-weight: 700;
  display: block;
  margin-bottom: 6px;
}

.file-note {
  color: #555555;
  font-size: 13px;
  margin: -4px 0 12px;
}

.profile-top {
  display: flex;
  align-items: center;
  gap: 14px;
}

.avatar {
  width: 84px;
  height: 84px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #159947;
  background: #f2f2f2;
}

.small-avatar {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #159947;
  background: #f2f2f2;
}

.profile-info h2 {
  font-size: 22px;
  margin-bottom: 4px;
}

.profile-info p {
  color: #333333;
  font-size: 14px;
}

.post-head {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 12px;
}

.post-head strong {
  display: block;
}

.post-head small {
  color: #555555;
}

.post-image {
  width: 100%;
  border-radius: 16px;
  margin: 8px 0 12px;
  object-fit: cover;
  max-height: 520px;
  background: #f2f2f2;
}

.caption {
  line-height: 1.4;
}

.preview {
  width: 100%;
  max-height: 280px;
  object-fit: cover;
  border-radius: 14px;
  margin-bottom: 12px;
  display: none;
  background: #f2f2f2;
}

.bottom-nav {
  position: fixed;
  left: 50%;
  bottom: 0;
  transform: translateX(-50%);
  width: 100%;
  max-width: 520px;
  background: #ffffff;
  border-top: 1px solid #e5e5e5;
  display: none;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
  padding: 10px;
}

.bottom-nav.active {
  display: grid;
}

.bottom-nav button {
  border-radius: 14px;
  padding: 11px 6px;
  font-size: 14px;
}

.empty {
  text-align: center;
  color: #555555;
  padding: 28px 10px;
  line-height: 1.4;
}

.stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  text-align: center;
  gap: 8px;
  margin-top: 16px;
}

.stat {
  background: #f6f6f6;
  border-radius: 14px;
  padding: 12px 6px;
}

.stat strong {
  display: block;
  font-size: 20px;
}

.stat span {
  font-size: 12px;
  color: #333333;
}

  </style>
</head>
<body>
  <div class="app">
    <header>
      <div class="logo">wild<span>cat</span></div>
      <button id="logoutBtn" class="ghost-btn" style="display:none;">Sair</button>
    </header><main>
  <section id="loginScreen" class="screen active">
    <div class="login-box card">
      <h1>wild<span style="color:#159947;">cat</span></h1>
      <p>Entre para postar fotos, ver o feed e editar seu perfil.</p>
      <input id="loginName" type="text" placeholder="Digite seu nome" />
      <button onclick="login()">Entrar</button>
    </div>
  </section>

  <section id="feedScreen" class="screen">
    <div id="feedList"></div>
  </section>

  <section id="createScreen" class="screen">
    <div class="card">
      <h2>Criar postagem</h2>
      <br />
      <label>Imagem da postagem</label>
      <input id="postImageInput" type="file" accept="image/*" />
      <p class="file-note">Escolha uma imagem do álbum/galeria. Não existe campo de URL.</p>
      <img id="postPreview" class="preview" alt="Prévia da postagem" />
      <textarea id="postCaption" placeholder="Escreva uma legenda..."></textarea>
      <button onclick="createPost()">Publicar</button>
    </div>
  </section>

  <section id="profileScreen" class="screen">
    <div class="card">
      <div class="profile-top">
        <img id="profileAvatar" class="avatar" alt="Foto de perfil" />
        <div class="profile-info">
          <h2 id="profileName">Usuário</h2>
          <p id="profileBio">Bem-vindo ao Wildcat.</p>
        </div>
      </div>

      <div class="stats">
        <div class="stat"><strong id="postCount">0</strong><span>posts</span></div>
        <div class="stat"><strong>128</strong><span>seguidores</span></div>
        <div class="stat"><strong>74</strong><span>seguindo</span></div>
      </div>
    </div>

    <div class="card">
      <h2>Editar perfil</h2>
      <br />
      <label>Nome</label>
      <input id="editName" type="text" placeholder="Seu nome" />

      <label>Bio</label>
      <textarea id="editBio" placeholder="Escreva sua bio"></textarea>

      <label>Foto de perfil</label>
      <input id="avatarInput" type="file" accept="image/*" />
      <p class="file-note">Escolha uma imagem do álbum/galeria. Não existe campo de URL.</p>
      <img id="avatarPreview" class="preview" alt="Prévia do perfil" />

      <button onclick="saveProfile()">Salvar perfil</button>
    </div>

    <div class="card">
      <h2>Minhas postagens</h2>
      <br />
      <div id="myPosts"></div>
    </div>
  </section>
</main>

<nav id="bottomNav" class="bottom-nav">
  <button onclick="showScreen('feedScreen')">Feed</button>
  <button onclick="showScreen('createScreen')">Postar</button>
  <button onclick="showScreen('profileScreen')">Perfil</button>
</nav>

  </div>  <script>
    const defaultAvatar = "data:image/svg+xml;utf8," + encodeURIComponent(`
      <svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'>
        <rect width='200' height='200' fill='#f2f2f2'/>
        <circle cx='100' cy='76' r='38' fill='#159947'/>
        <circle cx='100' cy='160' r='64' fill='#159947'/>
      </svg>
    `);

    let user = JSON.parse(localStorage.getItem("wildcatUser")) || null;
    let posts = JSON.parse(localStorage.getItem("wildcatPosts")) || [];
    let selectedPostImage = "";
    let selectedAvatarImage = "";

    const loginScreen = document.getElementById("loginScreen");
    const feedScreen = document.getElementById("feedScreen");
    const createScreen = document.getElementById("createScreen");
    const profileScreen = document.getElementById("profileScreen");
    const bottomNav = document.getElementById("bottomNav");
    const logoutBtn = document.getElementById("logoutBtn");

    function saveData() {
      localStorage.setItem("wildcatUser", JSON.stringify(user));
      localStorage.setItem("wildcatPosts", JSON.stringify(posts));
    }

    function login() {
      const name = document.getElementById("loginName").value.trim();
      if (!name) {
        alert("Digite seu nome para entrar.");
        return;
      }

      user = {
        name,
        bio: "Bem-vindo ao Wildcat.",
        avatar: defaultAvatar
      };

      saveData();
      startApp();
    }

    function logout() {
      user = null;
      localStorage.removeItem("wildcatUser");
      loginScreen.classList.add("active");
      feedScreen.classList.remove("active");
      createScreen.classList.remove("active");
      profileScreen.classList.remove("active");
      bottomNav.classList.remove("active");
      logoutBtn.style.display = "none";
    }

    function startApp() {
      bottomNav.classList.add("active");
      logoutBtn.style.display = "inline-block";
      showScreen("feedScreen");
      renderProfile();
      renderFeed();
    }

    function showScreen(screenId) {
      [loginScreen, feedScreen, createScreen, profileScreen].forEach(screen => {
        screen.classList.remove("active");
      });
      document.getElementById(screenId).classList.add("active");
      renderProfile();
      renderFeed();
      renderMyPosts();
    }

    function readImageFile(input, callback) {
      const file = input.files[0];
      if (!file) return;

      if (!file.type.startsWith("image/")) {
        alert("Escolha um arquivo de imagem.");
        input.value = "";
        return;
      }

      const reader = new FileReader();
      reader.onload = event => callback(event.target.result);
      reader.readAsDataURL(file);
    }

    document.getElementById("postImageInput").addEventListener("change", function () {
      readImageFile(this, image => {
        selectedPostImage = image;
        const preview = document.getElementById("postPreview");
        preview.src = image;
        preview.style.display = "block";
      });
    });

    document.getElementById("avatarInput").addEventListener("change", function () {
      readImageFile(this, image => {
        selectedAvatarImage = image;
        const preview = document.getElementById("avatarPreview");
        preview.src = image;
        preview.style.display = "block";
      });
    });

    function createPost() {
      const caption = document.getElementById("postCaption").value.trim();

      if (!selectedPostImage) {
        alert("Escolha uma imagem do álbum/galeria para publicar.");
        return;
      }

      const newPost = {
        id: Date.now(),
        author: user.name,
        avatar: user.avatar,
        image: selectedPostImage,
        caption: caption || "Sem legenda.",
        date: new Date().toLocaleString("pt-BR")
      };

      posts.unshift(newPost);
      selectedPostImage = "";
      document.getElementById("postImageInput").value = "";
      document.getElementById("postCaption").value = "";
      document.getElementById("postPreview").style.display = "none";
      saveData();
      showScreen("feedScreen");
    }

    function saveProfile() {
      const name = document.getElementById("editName").value.trim();
      const bio = document.getElementById("editBio").value.trim();

      user.name = name || user.name;
      user.bio = bio || user.bio;

      if (selectedAvatarImage) {
        user.avatar = selectedAvatarImage;
        selectedAvatarImage = "";
      }

      saveData();
      renderProfile();
      renderFeed();
      alert("Perfil salvo!");
    }

    function renderProfile() {
      if (!user) return;

      document.getElementById("profileName").textContent = user.name;
      document.getElementById("profileBio").textContent = user.bio;
      document.getElementById("profileAvatar").src = user.avatar || defaultAvatar;
      document.getElementById("editName").value = user.name;
      document.getElementById("editBio").value = user.bio;
      document.getElementById("postCount").textContent = posts.filter(post => post.author === user.name).length;
    }

    function postTemplate(post) {
      return `
        <article class="card">
          <div class="post-head">
            <img class="small-avatar" src="${post.avatar || defaultAvatar}" alt="Avatar" />
            <div>
              <strong>${escapeHTML(post.author)}</strong>
              <small>${post.date}</small>
            </div>
          </div>
          <img class="post-image" src="${post.image}" alt="Postagem" />
          <p class="caption"><strong>${escapeHTML(post.author)}</strong> ${escapeHTML(post.caption)}</p>
        </article>
      `;
    }

    function renderFeed() {
      const feedList = document.getElementById("feedList");
      if (!posts.length) {
        feedList.innerHTML = `<div class="empty card">Nenhuma postagem ainda.<br>Use o botão Postar para criar a primeira foto do Wildcat.</div>`;
        return;
      }
      feedList.innerHTML = posts.map(postTemplate).join("");
    }

    function renderMyPosts() {
      if (!user) return;
      const myPosts = posts.filter(post => post.author === user.name);
      const myPostsBox = document.getElementById("myPosts");

      if (!myPosts.length) {
        myPostsBox.innerHTML = `<div class="empty">Você ainda não criou postagens.</div>`;
        return;
      }

      myPostsBox.innerHTML = myPosts.map(postTemplate).join("");
    }

    function escapeHTML(text) {
      return String(text)
        .replaceAll("&", "&amp;")
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;")
        .replaceAll('"', "&quot;")
        .replaceAll("'", "&#039;");
    }

    logoutBtn.addEventListener("click", logout);

    if (user) {
      startApp();
    }
  </script></body>
</html>
