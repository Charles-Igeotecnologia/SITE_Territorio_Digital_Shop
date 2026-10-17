# Território Digital · Igeotecnologia

Projeto estático preparado para https://territoriodigital.shop/ em 17/10/2026. **Publicação não executada.**

O conteúdo, as cores, a tipografia, as marcas existentes e as imagens foram preservados. O original está entregue separadamente. Não há backend, banco de dados, instalação de Node.js na hospedagem ou etapa de build.

## Estrutura

- `index.html`: entrada do site, metadados do domínio e conteúdo estrutural.
- `assets/css/site.css`: estilos originais.
- `assets/js/app.js`: funcionalidades e CONFIG (contatos, setores, agenda e integrações).
- `assets/js/content.js`: 27 publicações e referências às imagens.
- `assets/vendor/leaflet/`: Leaflet 1.9.4 original e licença BSD-2.
- `postagens/_web/` e `assets/motion/`: 32 imagens extraídas sem recompressão.
- `.htaccess`: entrada index.html, bloqueio de listagem/pastas internas e cabeçalhos básicos.
- `robots.txt`, `sitemap.xml`: endereço oficial informado pelo proprietário.
- `docs/`: relatório, evidências e manifesto de preservação.
- `tests/`: regressão UTM e testes de navegador.

## Executar localmente

Na pasta do projeto, execute `python -m http.server 8080 --bind 127.0.0.1` e abra http://127.0.0.1:8080/. Use servidor HTTP para testar todas as funcionalidades.

## Testar

Node.js só é necessário para os testes. `npm ci` instala a dependência de desenvolvimento fixada; depois execute `npx playwright install chromium`. Rode `npm test` e, com o servidor local ativo, `npm run test:browser`.

Opcionalmente informe `CHROME_PATH` para usar Chrome instalado e `TEST_URL` para outro endereço local. O teste usa um navegador isolado, simula abertura do WhatsApp e não envia mensagens. A cópia de compartilhamento é testada com fallback de clipboard; a interface nativa de compartilhamento não é homologada. As capturas e os resultados são salvos em `docs/evidence/`.

## Dependências em produção

Leaflet está incluído no pacote. Google Fonts e mapas Esri precisam de internet. O mapa escuro foi removido a pedido do proprietário; ficam o satélite e os rótulos Esri. Os links do Hub levam a portais externos; o conteúdo desses portais não faz parte do projeto. Verifique condições de uso e limites dos provedores para o uso pretendido. Formspree e agenda incorporada estão desativados no original e não foram homologados.

## Publicar somente após confirmação

1. Confirmar repositório GitHub e visibilidade. A pasta local foi iniciada na branch `preparacao-publicacao`; nenhum repositório remoto foi criado e nenhum push foi feito.
2. Fazer backup integral do site e da configuração atual na Hostinger, incluindo arquivos ocultos. O domínio respondeu HTTPS 200 com título “Página padrão” no diagnóstico.
3. Revisar os contatos mantidos em CONFIG. Confirmar recebimento de e-mail e WhatsApp com o proprietário; os testes não enviaram mensagens.
4. Com autorização, versionar os arquivos e enviar ao repositório escolhido. Não incluir `.git`, `node_modules`, credenciais ou o HTML original de arquivo.
5. Na Hostinger, usar site **PHP/HTML personalizado**. Não há necessidade de contratar ambiente Node.js. Pelo painel do site, acessar **Avançado → Git**, conectar apenas o repositório escolhido e selecionar a branch aprovada. Conferir o destino `public_html`. Manter implantação automática desligada durante a revisão; não executar Deploy antes da aprovação.
6. Alternativa: enviar e extrair o conteúdo de `territorio-digital-publicacao.zip` diretamente em `public_html` pelo gerenciador de arquivos. O ZIP contém `index.html` na raiz, sem uma pasta intermediária. Preservar o backup antes de substituir qualquer arquivo existente.
7. Conferir certificado HTTPS, acesso pela raiz, imagem de compartilhamento, busca, leitor, bases do atlas, menu no celular e formulários. O `.htaccess` deve ser validado no servidor Hostinger; o servidor local Python não o interpreta.
8. Se houver regressão, restaurar o backup anterior. Não apagar os arquivos antigos antes de possuir cópia íntegra.

Não foi alterado DNS e não foi adicionada integração de publicação automática. `canonical`, `og:url`, imagem social, robots e sitemap já apontam para o domínio informado. As publicações continuam usando fragmentos `#post=...`; não há páginas individuais indexáveis para cada artigo.

Guia oficial consultado em 17/10/2026: https://www.hostinger.com/support/1583302-how-to-deploy-a-git-repository-in-hostinger/
