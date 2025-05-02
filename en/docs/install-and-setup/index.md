<div class="installAndSetup">
  <div class="section">
    <div class="text-block">
      <h1>MI for VS Code</h1>
      <p>A fully featured, AI powered low code IDE to develop, test, and deploy integration solutions</p>
      <a href="{{base_path}}/get-started/build-first-integration/first-integration-route-and-transform/" class="md-button md-button--primary">Get started →</a>
    </div>
    <div class="card">
      <img src="{{ base_path }}/assets/img/setup-and-install/vscode.png" alt="MI for VS Code preview">
    </div>
  </div>
  <div class="section">
    <div class="card">
      <img src="mi-runtime.png" alt="MI runtime preview">
    </div>
    <div class="text-block">
      <h1>Micro Integrator Runtime</h1>
      <p>A lightweight, cloud-native runtime for executing integration logic in production environments</p>
      <ul class="links-list">
        <li>
            <a href="" class="link">Prerequisites</a>
        </li>
        <li>
            <a href="" class="link">Download and run</a>
        </li>
        <li>
            <a href="" class="link">Configure</a>
        </li>
        <li>
            <a href="" class="link">Deploy</a>
        </li>
      </ul>
    </div>
  </div>
  <div class="section">
    <div class="text-block">
      <h1>Integration Control Plane</h1>
      <p>The Integration Control Plane provides a centralized interface for monitoring and managing deployed integrations. It allows you to track integration statuses, view logs, and manage services efficiently</p>
      <ul class="links-list">
        <li>
            <a href="" class="link">Prerequisites</a>
        </li>
        <li>
            <a href="" class="link">Download and run</a>
        </li>
        <li>
            <a href="" class="link">Configure</a>
        </li>
        <li>
            <a href="" class="link">Deploy</a>
        </li>
      </ul>
    </div>
    <div class="card">
      <img src="{{base_path}}/assets/img/get-started/build-first-integration/icp_home_page.png" alt="ICP preview">
    </div>
  </div>
</div>
{% raw %}
<style>
.md-sidebar.md-sidebar--secondary{
    display: none;
}
.section {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 40px;
    padding-bottom: 40px;
    margin-top: 40px;
    flex-wrap: nowrap;
    border-bottom: 1px solid rgba(175, 175, 175, 0.24);
    /* background:red; */
}
.section:last-of-type {
    border-bottom: none;
}
.text-block {
    flex: 1;
}
.text-block h1 {
    font-size: 2.5em;
    font-weight: 300;
    margin-bottom: 0.4em;
    color: var(----md-primary-fg-color-header);
}
.text-block p {
    margin-bottom: 1.5em;
}
.card {
    flex: 1;
    position: relative;
    overflow: hidden;
    padding: 10px;
}
.card img {
    outline: 1px solid rgba(0, 0, 0, 0.1);
}
.links-list li {
    list-style-type: none;
}
.link {
    /* font-size: 1.2em; */
    display: inline-block;
    margin-left: -30px;
    color: var(--text-color) !important;
    text-decoration: none;
}
.link:hover {
    color: rgb(255, 112, 67) !important;
    text-decoration: none;
}
.link:before {
    content: '→';
    font-weight: bold;
    margin-right: 5px;
}
@media (max-width: 900px) {
    .section {
    flex-direction: column;
    }
}
</style>
{% endraw %}
