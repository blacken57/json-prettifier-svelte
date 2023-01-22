<nav class="navbar">
  <div class="brand-title">Json Prettifier</div>
  <a href="#" class="toggle-button">
    <span class="bar"></span>
    <span class="bar"></span>
    <span class="bar"></span>
  </a>
  <div class="navbar-links">
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </div>
</nav>

<script>

</script>

<style>
    * {
    box-sizing: border-box;
    }

    .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #05386B;
    color: #fff;
    }

    .brand-title {
    font-size: 1.5rem;
    margin: 0.8rem;
    }

    .navbar-links ul {
    margin: 0;
    padding: 0;
    display: flex;
    }

    .navbar-links li {
    list-style: none;
    }

    .navbar-links li:hover {
    background-color: #555;
    }

    .navbar-links li a {
    text-decoration: none;
    color: white;
    padding: 1rem;
    display: block;
    }

    .toggle-button {
    position: absolute;
    top: 1rem;
    right: 1rem;
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 28px;
    height: 21px;
    }

    .toggle-button .bar {
    height: 3px;
    width: 100%;
    background-color: white;
    border-radius: 10px;
    }

    @media (max-width: 400px) {
        .toggle-button {
            display: flex;
        }

        .navbar {
            flex-direction: column;
            align-items: flex-start;
        }

        .navbar-links {
            display: none;
            width: 100%;
        }

        .navbar-links ul {
            width: 100%;
            flex-direction: column;
        }

        .navbar-links li {
            text-align: center;
        }

        .navbar-links li a {
            padding: 0.5rem 1rem;
        }

        .navbar-links.active {
            display: flex;
        }
    }
</style>