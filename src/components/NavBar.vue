<template>
  <header>
    <nav class="navbar navbar-expand">
      <div class="container-fluid">
        <div class="collapse navbar-collapse justify-content-center" id="navbarSupportedContent">
          <ul class="nav-list navbar-nav mb-2 mb-lg-0">
            <li class="nav-item">
              <RouterLink class="nav-link" to="/">Primeira geração</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/geracao2">Segunda geração</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/geracao3">Terceira geração</RouterLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<style scoped>
.navbar {
  background-color: #181b1d;
}

.nav-item .nav-link {
  color: white;
  font-size: 18px;
  border: 1px solid white;
  border-radius: 10px;
  margin: 10px;
  transition: all 0.4s;
}

.nav-item .nav-link:hover {
  color: green;
  border-color: green;
}

@media (max-width: 576px) {
  .nav-list {
    display: flex;
    flex-direction: column;
    width: 100%;
    text-align: center;
  }
}
</style>
