# GoNa — Georreferenciamento

Código da versão 16, publicada em 16/10/2026.

## Executar
Requer Python 3 apenas para servir os arquivos localmente:

    python -m http.server 8080 --directory dist

Abra http://localhost:8080. Para usar GPS no celular, publique a pasta dist em hospedagem HTTPS.

## Estrutura
- dist/index.html: interface, mapa e coleta GPS
- dist/file-formats.js: exportação de dados
- dist/file-import.js: importação vetorial
- dist/file-manager.js: gestão de arquivos
- dist/files.css: estilos
- dist/service-worker.js e manifest.webmanifest: instalação como PWA
- dist/assets e dist/icons: marca e ícones

## Estado atual
Aplicativo web estático/PWA, em HTML, CSS e JavaScript. O mapa usa Leaflet e imagens de serviços externos. Os dados são armazenados no navegador/aparelho (localStorage); esta versão não tem backend, autenticação própria ou integração com Supabase.

Importação: GeoJSON/JSON, KML/KMZ, GPX, CSV, Shapefile ZIP e DXF conforme a referência espacial suportada. PDF e GeoPDF abrem para visualização; o georreferenciamento do GeoPDF ainda não é aplicado como camada no mapa.

Os levantamentos salvos no celular não fazem parte deste ZIP. Exporte-os pelo aplicativo para fazer backup.

Não há etapa de compilação nem dependências npm. Leaflet e serviços de mapa exigem conexão quando ainda não disponíveis em cache.


## v17 — navegação e mapa
- Mapa com rotação por gesto e orientação automática pela bússola do aparelho quando disponível.
- Controle de bússola para retornar o mapa ao Norte.
- Cursor de localização em formato de gota direcional.
- Zoom do mapa ampliado até o limite da interface; a imagem Esri é ampliada além do nível nativo para evitar solicitar tiles inexistentes em níveis superiores.
