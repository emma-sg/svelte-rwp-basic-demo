<script>
  const replayWebURL = "https://cdn.jsdelivr.net/npm/replaywebpage@2.0.0/ui.js";

  const isScriptAlreadyIncluded = (src) => {
    const scripts = document.getElementsByTagName("script");
    for (let i = 0; i < scripts.length; i++)
      if (scripts[i].getAttribute("src") === src) return true;
    return false;
  };

  const loadScript = async (url) =>
    new Promise((resolve) => {
      if (!isScriptAlreadyIncluded(url)) {
        const script = document.createElement("script");
        script.onload = () => {
          resolve();
        };
        script.src = url;
        document.head.appendChild(script);
      } else {
        resolve();
      }
    });

  (async () => {
    try {
      await loadScript(replayWebURL);
    } catch (e) {
      console.error(e);
    }
  })();
</script>

<h1>Svelte RWP Example</h1>
<replay-web-page
  style="height: 600px;"
  source="https://replayweb.page/docs/examples/tweet-example.wacz"
  replayBase="arbitrarySWPath/"
></replay-web-page>
