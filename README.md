# dio-lab-assistente-investimentos-rpa-n8n-desafioF
Desafio Final DIO + Santander — Assistente de Investimentos com RPA e n8n de forma segura, didática e verificável.

1. Precisa estar pronto antes da entrega
   
1. Notebook Python no Google Colab

Extrai os clientes do HTML com Requests e BeautifulSoup, valida os dados e prepara o JSON.

Evidência: execução real das células e resumo dos registros extraídos.

2. Workflow no n8n

Recebe o JSON, lê a base CSV, cruza perfil e saldo mínimo e devolve uma resposta JSON.

Evidência: workflow importado e execução sem erros.

3. Repositório GitHub organizado

Reúne notebook, workflow, README, documentação, instruções de execução e testes.

Evidência: arquivos publicados e acessíveis no repositório.

4. Entrega na plataforma DIO

Apresenta o objetivo, as tecnologias, o repositório e os resultados efetivamente comprovados. 
Evidência: confirmação de envio ou conclusão na própria plataforma. 

Importante: ter os arquivos preparados não significa que a automação está concluída. Vamos distinguir preparação, execução e publicação em cada etapa.

2. Acesse o desafio correto na DIO
   
1. Entre na plataforma DIO e faça login com a conta vinculada ao seu bootcamp.
2. Abra a trilha Santander — Automações com n8n.
3. Localize o módulo do Desafio Final.
4. Abra o enunciado e procure a seção “Entendendo o Desafio”, ou equivalente.
5. Confira quais itens a plataforma solicita para a entrega: normalmente, em desafios de projeto, o repositório GitHub é um elemento importante; confirme o formato exigido no seu enunciado específico. 

Antes de começar: mantenha aberta a página do desafio para consultar os critérios oficiais durante a implementação. Se houver exigência de vídeo, apresentação ou formato específico de repositório, ela prevalece sobre o roteiro geral abaixo.

3. Prepare o repositório GitHub
Seu repositório de referência é:
Abrir seu repositório no GitHubO projeto deve continuar sendo o Assistente de Investimentos com RPA e n8n. Não substitua a página HTML e o CSV de referência existentes: eles fazem parte da base que será utilizada na automação.
Estrutura final esperada
dio-lab-assistente-investimentos-rpa-n8n/

README.md

ENTREGA_DIO.md

rpa/

extrair_clientes.ipynb

n8n/

workflow.json

docs/

arquitetura.md

testes.md

seguranca.md

evidencias/README.md

Preservar também index.html e data.csv, se já estiverem nessa pasta.

.gitignore

.env.example

Atenção: os nomes acima representam a organização esperada. Nesta conversa, não foi possível gerar e validar o pacote ZIP para download; portanto, não presuma que todos esses arquivos já estejam no seu computador ou no GitHub.

4. Confira os requisitos oficiais do projeto
Consulte o README do seu repositório. Ele apresenta o objetivo e os entregáveis do desafio. 

O roteiro do projeto separa dois níveis:
Requisito	MVP	Desafio completo
Extração dos clientes com Python	Obrigatório	Obrigatório
Webhook integrado ao n8n	Obrigatório	Obrigatório
Leitura do CSV e cruzamento dos dados	Obrigatório	Obrigatório
Mensagens personalizadas por perfil	Templates estáticos	Geração dinâmica com IA
Workflow exportado em JSON	Obrigatório	Obrigatório
Evidência do fluxo ponta a ponta	Obrigatório	Obrigatório
Documentação das decisões técnicas	Recomendável e prevista no projeto completo	Incluída

Um ajuste importante: o workflow candidato descrito anteriormente valida e cruza dados, mas isso, sozinho, não comprova a geração das mensagens personalizadas solicitadas pelo MVP. Você deverá acrescentar essa etapa antes de considerar o projeto pronto para entrega.

O CSV de referência contém os campos perfil, produto, minimo e rentabilidade. A página HTML tem 10 clientes fictícios. 

5. Execute o notebook no Google Colab
Abra o Google Colab.

1. Acesse Arquivo → Fazer upload de notebook.
2. Selecione extrair_clientes.ipynb no seu computador.
3. Execute as células na ordem, usando o botão de execução de cada célula.
4. Confira se a página HTML foi acessada e se os registros foram extraídos.
5. Verifique se os saldos foram interpretados corretamente, por exemplo, R$ 12.500,00 como 12500.00.
6. Confirme que o CSV foi acessado e que as quatro colunas esperadas foram identificadas.
7. Resolva os erros que aparecerem antes de avançar.
O notebook de referência está no repositório-base da DIO. Se preferir, você pode utilizá-lo como ponto de partida, mas precisa completar e testar a integração solicitada.
O que registrar como evidência
- Captura da extração dos clientes.
- Captura da leitura do CSV.
- Resumo de quantos registros foram processados e quantos precisam de revisão.
Não marque essa etapa como concluída se apenas abriu o notebook. As células precisam ser executadas com sucesso.

6. Importe e configure o workflow no n8n
Acesse sua instância do n8n. Você pode usar a versão em nuvem ou uma instalação local.
Passo a passo

1. Abra a área de workflows.
2. Selecione a opção de importar workflow a partir de arquivo.
3. Importe n8n/workflow.json.
4. Confira se os nós e as conexões aparecem corretamente.
5. Abra o nó HTTP Request e confirme a URL do CSV.
6. Execute esse nó isoladamente e confira se a saída contém os dados da base.
7. Configure o nó Webhook para receber requisições POST.
8. Confira se o nó de processamento valida os dados, cruza perfil e saldo mínimo e produz uma mensagem para cada cliente.
9. Configure o nó final para devolver a resposta em JSON.
Como devem funcionar as mensagens
O MVP pode utilizar mensagens estáticas condicionadas ao perfil, conforme o enunciado. Por exemplo:
- Conservador: mensagem informativa sobre características, liquidez e riscos das opções cadastradas.
- Moderado: mensagem informativa sobre a diversidade de características e os riscos das opções da base.
- Arrojado: mensagem informativa sobre a variabilidade dos resultados e os riscos associados às opções cadastradas.
Essas mensagens são exemplos de conteúdo a implementar, não resultados de uma execução já realizada. Não devem apresentar rentabilidades como garantidas nem substituir uma avaliação financeira profissional.

A integração com IA generativa pode ser feita como etapa adicional, após o MVP funcionar.
7. Teste a integração ponta a ponta
Esta é a etapa mais importante para demonstrar que você realmente desenvolveu a automação.

Teste 1 — Iniciar o webhook

No n8n, use a opção de escutar eventos de teste e copie a URL temporária apresentada.

Teste 2 — Enviar os clientes

No notebook do Colab, informe a URL do webhook e execute a célula que envia o JSON.
Teste 3 — Conferir todos os nós

Confirme se o webhook recebeu o lote, se o CSV foi lido, se o cruzamento foi executado e se as mensagens foram geradas.


Teste 4 — Conferir a resposta

Verifique se o notebook recebeu a resposta HTTP e se o JSON contém os resultados esperados, sem erros inesperados.

Se um nó falhar, abra sua saída e examine a mensagem de erro. Não presuma que a automação funcionou só porque o webhook recebeu uma requisição.

Atenção: a URL de teste do n8n costuma depender de uma sessão de escuta ativa. Para o teste de produção, você deverá ativar o workflow e utilizar a URL de produção. Não publique URLs privadas ou credenciais em capturas de tela.
8. Organize as evidências e a documentação
No repositório, crie ou atualize a pasta docs/evidencias/.

Registre capturas reais dos seguintes itens:
Checklist de evidências

[ ] Notebook executado e clientes extraídos
[ ] CSV lido e colunas identificadas
[ ] Workflow completo aberto no editor n8n
[ ] Saída do nó que consulta o CSV
[ ] Execução ponta a ponta sem erros
[ ] Resposta JSON recebida pelo notebook
[ ] Mensagens personalizadas geradas por perfil
Copiar checklist
Não é necessário inserir dados pessoais reais. Utilize os dados fictícios do projeto e oculte tokens, URLs privadas e outras informações sensíveis.

Atualize também:
- README.md: objetivo, arquitetura, configuração e instruções para reproduzir o fluxo.
- docs/arquitetura.md: nós, conexões e contrato de dados.
- docs/testes.md: cenários executados, resultados e falhas encontradas.
- docs/seguranca.md: tratamento de credenciais e limitações.
- ENTREGA_DIO.md: apresentação resumida do projeto.
  
9. Publique os arquivos no GitHub
A maneira mais simples para quem está começando é usar o GitHub Desktop. Outra possibilidade é enviar os arquivos pela interface web do GitHub.
Opção recomendada: GitHub Desktop
1. Instale o GitHub Desktop.
2. Faça login na sua conta.
3. Clone o repositório MychelleJacob/dio-lab-assistente-investimentos-rpa-n8n.
4. Copie os arquivos finais para as pastas correspondentes.
5. Preserve docs/index.html e docs/data.csv.
6. Revise a lista de alterações.
7. Confirme que nenhum segredo ou arquivo privado está sendo enviado.
8. Escreva uma mensagem de commit, por exemplo: feat: integra RPA Python com workflow n8n.
9. Clique em Commit to main e depois em Push origin.
Depois, abra o repositório no navegador e confirme se os arquivos aparecem na branch main.

Se preferir utilizar comandos Git, faça isso dentro de uma cópia local atualizada do seu repositório:
git status
git add README.md ENTREGA_DIO.md .gitignore .env.example rpa/ n8n/ docs/
git commit -m "feat: integra RPA Python com workflow n8n"
git push origin main


Execute os comandos apenas depois de copiar os arquivos e revisar as alterações. Se houver arquivos modificados que não pertencem ao desafio, examine-os antes de incluir no commit.

10. Envie o projeto na plataforma DIO
Com o repositório publicado e os testes concluídos:

1. Retorne ao módulo do Desafio Final na DIO.
2. Abra novamente o enunciado e os critérios de entrega.
3. Localize o campo de submissão do projeto.
4. Se o formulário solicitar o repositório, cole o endereço:
   
   https://github.com/MychelleJacob/dio-lab-assistente-investimentos-rpa-n8n
   
6. Preencha eventuais campos adicionais solicitados pelo enunciado, como descrição ou link de demonstração.
7. Revise se o repositório está público e acessível sem login.
8. Confirme o envio.
9. Verifique se a plataforma apresenta uma confirmação de entrega ou altera o status da atividade.
A documentação da DIO destaca a importância de apresentar o projeto por meio do GitHub em desafios de projeto. Confirme sempre as instruções específicas da sua atividade.

11. Checklist final de conformidade
Use esta lista antes de considerar a entrega concluída.

Progresso da entrega 
[ ] Li os critérios oficiais do Desafio Final
[ ] Notebook executado com sucesso no Colab
[ ] Extração e leitura do CSV verificadas
[ ] Workflow importado e executado no n8n
[ ] Mensagens estáticas por perfil implementadas
[ ] Integração ponta a ponta comprovada
[ ] Evidências reais salvas
[ ] README e documentação atualizados
[ ] Arquivos publicados no GitHub
[ ] Repositório conferido no navegador
[ ] Projeto enviado na DIO e confirmação verificada
Copiar checklist final

OBS: Começar pela execução do notebook e pela montagem do workflow no n8n. Em seguida, validar o envio e a resposta JSON, implementar as mensagens por perfil e só então publicar a versão final.
O repositório já fornece a base HTML e o CSV necessários para orientar o trabalho. 
O que ainda precisa ser comprovado é a execução real do fluxo completo e a geração das mensagens. 
