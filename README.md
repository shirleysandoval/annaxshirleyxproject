<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: #333;
    background-color: #fcfcfc;
    line-height: 1.6;
  }
  
  .main-header {
    background: linear-gradient(135deg, #1e5299 0%, #2980b9 100%);
    color: white;
    padding: 30px;
    border-radius: 8px;
    margin-bottom: 30px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }
  
  .main-header h1 { margin: 0; font-size: 2.5rem; }
  .main-header p { margin: 5px 0 0 0; opacity: 0.9; font-size: 1.1rem; }

  .project-section {
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
    background: white;
    padding: 25px;
    border-radius: 8px;
    border-left: 5px solid #2980b9;
    margin-bottom: 35px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
  }

  .section-text { flex: 2; min-width: 300px; }
  .section-image { flex: 1; min-width: 200px; display: flex; align-items: flex-start; justify-content: center; padding-top: 10px; }
  
  .section-image img {
    width: 100%;
    max-width: 180px;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    object-fit: cover;
  }

  .code-container {
    background-color: #f8f9fa;
    border: 1px solid #e1e4e6;
    border-radius: 6px;
    padding: 15px;
    font-family: 'Courier New', Courier, monospace;
    font-size: 0.85rem;
    overflow-x: auto;
    white-space: pre-wrap;
    color: #2c3e50;
    margin-top: 10px;
    margin-bottom: 15px;
  }

  .code-title {
    font-weight: bold;
    color: #7f8c8d;
    font-size: 0.8rem;
    text-transform: uppercase;
    margin-top: 15px;
  }

  /* Estilos para las tablas de resultados de datos */
  .data-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 10px;
    font-size: 0.9rem;
  }
  .data-table th {
    background-color: #f1f2f6;
    color: #2c3e50;
    text-align: left;
    padding: 8px 12px;
    border-bottom: 2px solid #dcdde1;
  }
  .data-table td {
    padding: 8px 12px;
    border-bottom: 1px solid #f1f2f6;
  }
  .data-table tr:hover { background-color: #f8f9fa; }

  .project-footer {
    background-color: #f1f2f6;
    padding: 20px;
    border-radius: 8px;
    margin-top: 50px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    font-size: 0.95rem;
    border-top: 2px solid #dcdde1;
  }
  .footer-team { font-weight: bold; color: #2c3e50; }
  .footer-method { font-style: italic; color: #7f8c8d; }
</style>

<div class="main-header">
  <h1>annaxshirleyxproject</h1>
  <p>Final Project: Computer Studies and Humanities</p>
</div>

<h2>Research Questions & SPARQL Queries</h2>
<p>Below you will find the results and data structures for our investigation into Italian literature.</p>

<hr style="border: 0; border-top: 1px solid #e1e4e6; margin: 20px 0;">

<div class="project-section">
  <div class="section-text">
    <h3 style="margin-top:0; color:#2980b9;">Birthplaces and Regions</h3>
    
    <div class="code-title">SPARQL Query</div>
    <div class="code-container">PREFIX wd: &lt;http://www.wikidata.org/entity/&gt;
PREFIX wdt: &lt;http://www.wikidata.org/prop/direct/&gt;
PREFIX wikibase: &lt;http://wikidata.org/ontology#&gt;
PREFIX bd: &lt;http://www.bigdata.com/rdf#&gt;

SELECT ?authorLabel ?placeLabel ?regionLabel WHERE {
  VALUES ?author { wd:Q1067 wd:Q1064 wd:Q12807 }
  ?author wdt:P19 ?place .
  ?place wdt:P131 ?region .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}</div>

    <div class="code-title" style="color:#2c3e50;">Query Results (Information)</div>
    <table class="data-table">
      <thead>
        <tr>
          <th>Author</th>
          <th>Birthplace</th>
          <th>Region</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Dante Alighieri</td>
          <td>Florence</td>
          <td>Tuscany</td>
        </tr>
        <tr>
          <td>Alessandro Manzoni</td>
          <td>Milan</td>
          <td>Lombardy</td>
        </tr>
        <tr>
          <td>Umberto Eco</td>
          <td>Alessandria</td>
          <td>Piedmont</td>
        </tr>
      </tbody>
    </table>
  </div>
  <div class="section-image">
    <img src="https://images.unsplash.com/photo-1543002588-bfa74002ed7e?w=400&auto=format&fit=crop&q=60" alt="Books and History">
  </div>
</div>

<div class="project-section" style="border-left-color: #e74c3c;">
  <div class="section-text">
    <h3 style="margin-top:0; color:#e74c3c;">Media and Film Adaptations</h3>
    
    <div class="code-title">SPARQL Query</div>
    <div class="code-container">PREFIX wd: &lt;http://www.wikidata.org/entity/&gt;
PREFIX wdt: &lt;http://www.wikidata.org/prop/direct/&gt;
PREFIX wikibase: &lt;http://wikidata.org/ontology#&gt;
PREFIX bd: &lt;http://www.bigdata.com/rdf#&gt;

SELECT ?authorLabel ?workLabel ?adaptationLabel WHERE {
  VALUES ?author { wd:Q1067 wd:Q1064 wd:Q12807 }
  ?work wdt:P50 ?author .
  ?work wdt:P4969 ?adaptation .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}</div>

    <div class="code-title" style="color:#2c3e50;">Query Results (Information)</div>
    <table class="data-table">
      <thead>
        <tr>
          <th>Author</th>
          <th>Work / Book</th>
          <th>Film / TV Adaptation</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Dante Alighieri</td>
          <td>Inferno</td>
          <td>L'Inferno (1911 Movie)</td>
        </tr>
        <tr>
          <td>Alessandro Manzoni</td>
          <td>I Promessi Sposi</td>
          <td>The Betrothed (TV Series)</td>
        </tr>
        <tr>
          <td>Umberto Eco</td>
          <td>Il nome della rosa</td>
          <td>The Name of the Rose (Film & Series)</td>
        </tr>
      </tbody>
    </table>
  </div>
  <div class="section-image">
    <img src="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?w=400&auto=format&fit=crop&q=60" alt="Cinema and Film">
  </div>
</div>

<div class="project-section" style="border-left-color: #2ecc71;">
  <div class="section-text">
    <h3 style="margin-top:0; color:#2ecc71;">Literary Themes</h3>
    
    <div class="code-title">SPARQL Query</div>
    <div class="code-container">PREFIX ex: &lt;http://example.org/literature/&gt;
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;

SELECT ?authorName ?workTitle ?themeValue WHERE {
  VALUES (?authorName ?work) {
    ("Dante Alighieri" ex:TheDivineComedy)
    ("Dante Alighieri" ex:VitaNuova)
    ("Alessandro Manzoni" ex:Adelchi)
    ("Alessandro Manzoni" ex:IlCinqueMaggio)
    ("Umberto Eco" ex:FoucaultsPendulum)
    ("Umberto Eco" ex:ThePragueCemetery)
  }
  ?work ex:hasTheme ?themeValue .
  BIND(STRAFTER(STR(?work), "literature/") AS ?workTitle)
}
ORDER BY ?authorName ?workTitle</div>

    <div class="code-title" style="color:#2c3e50;">Query Results (Information)</div>
    <table class="data-table">
      <thead>
        <tr>
          <th>Author</th>
          <th>Literary Work</th>
          <th>Associated Themes</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Dante Alighieri</td>
          <td>The Divine Comedy</td>
          <td>Divine Justice, Soul Redemption, Sin and Punishment</td>
        </tr>
        <tr>
          <td>Dante Alighieri</td>
          <td>Vita Nuova</td>
          <td>Courtly Love, Spiritual Transformation, Grief</td>
        </tr>
        <tr>
          <td>Alessandro Manzoni</td>
          <td>Adelchi</td>
          <td>Historical Injustice, Political Betrayal</td>
        </tr>
        <tr>
          <td>Alessandro Manzoni</td>
          <td>Il Cinque Maggio</td>
          <td>Human Glory, Fragility of Power, Divine Faith</td>
        </tr>
        <tr>
          <td>Umberto Eco</td>
          <td>Foucault's Pendulum</td>
          <td>Conspiracy Theories, Hermetic Secret, Intellectual Satire</td>
        </tr>
        <tr>
          <td>Umberto Eco</td>
          <td>The Prague Cemetery</td>
          <td>Antisemitism, Psychological Manipulation, Historical Forgery</td>
        </tr>
      </tbody>
    </table>
  </div>
  <div class="section-image">
    <img src="https://images.unsplash.com/photo-1456513080510-7bf3a84b82f8?w=400&auto=format&fit=crop&q=60" alt="Literature and Study">
  </div>
</div>

<div class="project-footer">
  <div class="footer-team">👥 Team: Anna Shirley & Shirley Sandoval</div>
  <div class="footer-method">📖 Methodology: Italian Literature as Cultural Identity</div>
</div>
