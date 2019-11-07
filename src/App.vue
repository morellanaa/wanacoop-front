<template>
  <div id="app">
		<div id="nav">
			<b-navbar toggleable="sm" type="light" variant="light">
				<b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>
				<b-navbar-brand to="/">Wanacoop</b-navbar-brand>
				<b-collapse id="nav-text-collapse" is-nav>
					<b-navbar-nav>
						<b-nav-item to="/panicbutton">Panic Button</b-nav-item>
						<b-nav-item to="/map">Map Overview</b-nav-item>
						<b-nav-item to="/protestnav">Protest Nav</b-nav-item>
					</b-navbar-nav>
				</b-collapse>
			</b-navbar>
		</div><br>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
