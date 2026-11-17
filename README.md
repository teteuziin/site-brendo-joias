# Site — Brendo Joias (@brendojoias_ssa)

Site-modelo da fase 2 da missão de prospecção (empresa nº5), construído a partir do portfólio real da joalheria. **NÃO PUBLICAR sem aprovação do usuário** — publicação no GitHub/Pages somente após o OK dele.

## Conceito — "A Vitrine"
A vitrine permanente que ela não tem. A própria dona explica no vídeo de dúvidas frequentes que os preços vivem nos Stories porque no feed desatualizam; o site é a vitrine dela, sempre no ar: preto profundo das vitrines da loja + dourado da marca, peças apresentadas em molduras de filete duplo dourado (a "vitrine iluminada"), serifada elegante (Cormorant Garamond) + Archivo. Um único acento: o dourado.

## Estrutura
- `index.html` — página única (intro temática ≤1,6s pulável com varredura dourada, hero com logo oficial e vídeo institucional, A Vitrine com filtro por categoria, Alianças com carrossel do catálogo dela + montador de orçamento que abre o WhatsApp dela com a mensagem montada, Preço justo com os únicos preços que ela publica + vídeo da vitrine + vídeo FAQ, Compro ouro com a arte oficial dela, Atendimento de verdade com a conversa real de WhatsApp, A Loja com inauguração e tour, rodapé com WhatsApp/Instagram e botão flutuante de WhatsApp)
- `media/` — 14 vídeos reais dela (todos com áudio AAC), pôsteres extraídos de frames reais dos próprios vídeos, fotos dos carrosséis-catálogo dela (alianças e correntes/pingentes), arte oficial "Compro Ouro" e a logo oficial

## Logo sem fundo (instrução do usuário)
A oficial (`brendo-joias-portfolio/marca/logo-oficial-transparente.png`) **já é transparente** — entrou no pacote como está (`media/logo.png`, bytes idênticos ao arquivo da coleta). Por ser dourada, é usada sempre sobre o preto da identidade. No cabeçalho/rodapé, a exibição usa uma janela com recorte visual via CSS (a arte é centralizada no quadro 800×800; o CSS mostra a faixa central) — o arquivo não foi alterado.

## Conteúdo — só o verificado (ficha: ../brendo-joias-portfolio/README.md)
- Slogan dela: "O luxo que aproxima você do extraordinário" (letreiro da loja e página de links)
- Fatos: desde 2018 · mais de 10 anos na área de joias · envio para todo o Brasil · loja física inaugurada em out/2025
- WhatsApp público confirmado (publicado por ela): (71) 99158-4648 — todos os CTAs apontam para ele; o montador de alianças monta a mensagem e abre o wa.me dela
- Preços — SOMENTE os publicados por ela: pingentes de cruz com pedras naturais 10x de R$ 550 ou R$ 4.950 no Pix; etiquetas da vitrine R$ 7.500 e R$ 4.400; anel de esmeralda de R$ 4.000 a R$ 7.000. Os preços da varredura (corrente R$ 5.700, pingente R$ 3.150) NÃO foram localizados no feed — ficaram fora
- Serviços confirmados: pronta-entrega em ouro 18k com pedras naturais (sem banhado/folheado), alianças sob orçamento, encomendas pelo Direct, compra de ouro com Pix na hora, prata
- Endereço: somente "Av. Paralela, Salvador" (o completo não é público — ela repassa no Direct; o site tem botão "pedir a localização no WhatsApp"). **Horários não são públicos — omitidos, nada inventado**

## Escolhas sinalizadas
- **Nome da dona: não aparece.** Não foi localizado em nenhuma fonte pública; o site fala na voz da marca (1ª pessoa) e se refere a ela só como "a dona" onde o vídeo institucional pede.
- **Carrossel de alianças: slide duplicado removido.** Os slides 1 e 3 do post são o mesmo arquivo (md5 idêntico: 0728e0e6…); o site usa as 4 imagens únicas (slides 1, 2, 4, 5), cada uma uma vez.
- **Vídeo 09 (FAQ) recomprimido:** o original tinha 25,4 MB (acima do limite de 25 MB/arquivo do GitHub). Recomprimido para 15,6 MB (H.264 CRF 26, teto 1800 kbps), mantendo 720×1280 e o áudio AAC — conferido por ffprobe.
- **Vídeos 360×640** (02-inauguração, 05-vitrine-precos, 14-trevo-sorte): exibidos contidos em molduras de no máximo ~320px de largura — nunca esticados nem como fundo.
- **Fotos dos carrosséis dela trazem texto/marca d'água da própria marca** (as páginas do catálogo de alianças são artes dela; os closes de correntes têm a assinatura "Brendo joias Bj" dela). São o portfólio oficial publicado por ela — mantidos como estão; as legendas do site ficam sempre abaixo da mídia, nunca sobrepostas. Os slides de correntes foram redimensionados para no máximo 1600px (originais de até 4096px) só para peso de web.
- Fora do site, de propósito: conserto, gravação, polimento, fabricação própria e venda de relógios (não confirmados — relógios só aparecem dentro das vitrines dos vídeos), Black Friday (vigência não confirmada), sorteio encerrado, endereço completo e horários (não públicos).

## Checagens feitas na construção
- ffprobe arquivo a arquivo no pacote final: 14/14 vídeos com faixa de áudio AAC; resoluções conferidas (720×1280 ×11; 360×640 ×3, contidos); maior arquivo 17,5 MB (institucional) — todos abaixo de 25 MB; pacote total ~76 MB
- Interações testadas em jsdom (43 asserções, 0 falhas): intro que fecha no clique, menu mobile, reveal por interseção, pausa de vídeo fora da tela (e não-retomada; hero ambiente mudo retoma), botão "Ouvir com som" do hero (desmuta, ganha controls, sai do modo ambiente), filtro da vitrine (contagens por categoria: anéis 2, correntes 10, pulseiras 1, conjuntos 3, todas 16), carrossel de alianças (setas, pontos, wrap, legendas), montador de orçamento (largura só no par simples; medidas; href do wa.me carregando exatamente a mensagem montada), ano dinâmico do rodapé
- Contraste calculado: 13 pares texto×fundo, todos WCAG AA — pior caso 7,65:1 (dourado sobre superfície, nos rótulos do montador); texto principal 17,12:1
- Anti-duplicação: cada preço e cada fato aparece 1× no texto (R$ 550, R$ 4.950, R$ 4.400, R$ 7.500, R$ 4.000, R$ 7.000, Av. Paralela, envio para todo o Brasil, 10 anos, Pix na hora); termos proibidos com 0 ocorrências (conserto, gravação, polimento, Black Friday, sorteio, relógio, horário, preços da varredura)
- Todas as 43 referências de mídia do HTML (29 em src/href + 14 pôsteres) resolvem para arquivos do pacote; zero base64/data URI; cursor apenas o nativo
