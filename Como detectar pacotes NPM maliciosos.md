
![NPM Image](https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Npm-logo.svg/120px-Npm-logo.svg.png)
# Como detectar e evitar pacotes NPM maliciosos

Detectar pacotes NPM maliciosos é um desafio importante para garantir a segurança de seus projetos. Aqui estão algumas práticas para identificar pacotes potencialmente maliciosos:

### 1. **Verifique a Popularidade e a Reputação**
   - **Downloads**: Confira o número de downloads do pacote no [site oficial do NPM](https://www.npmjs.com/). Pacotes com muitos downloads são mais confiáveis, mas não garantem segurança.
   - **Estrelas no GitHub**: Se o pacote tiver um repositório no GitHub, verifique o número de estrelas e bifurcações (forks). Também procure por contribuições recentes e mantenedores ativos.
   - **Histórico de Versões**: Observe a frequência de atualização e mudanças na versão para identificar padrões anormais.

### 2. **Análise de Dependências**
   - Utilize ferramentas como [NPM Audit](npm-audit.md) para detectar vulnerabilidades conhecidas.
   - Verifique manualmente o arquivo `package.json` para garantir que não haja dependências estranhas.

### 3. **Verifique o Código Fonte**
   - Sempre prefira pacotes que possuem um repositório público (como no GitHub) e revise o código fonte para comportamentos suspeitos.
   - Procure por scripts de pós-instalação (`postinstall`), chamadas de rede inesperadas, execução de código de maneira dinâmica ou códigos ofuscados.

### 4. **Procure por Nomes Semelhantes**
   - Um método comum de ataque é a typosquatting (criação de pacotes com nomes semelhantes a pacotes legítimos, como `reacts` em vez de `react`).
   - Tenha atenção a pequenas variações nos nomes dos pacotes antes de instalar.

### 5. **Revise os Scripts e Eventos de Lifecycle**
   - Abra o `package.json` e revise as entradas em `"scripts"` para identificar comandos que serão executados automaticamente (como `preinstall`, `postinstall`, etc.).
   - Desconfie de pacotes que incluem muitas execuções de script durante a instalação.

### 6. **Utilize Ferramentas de Segurança**
   - **npm audit**: Executa uma verificação de vulnerabilidades conhecidas em suas dependências.
   - **snyk**: Uma ferramenta de segurança que pode ser usada para escanear seus pacotes em busca de vulnerabilidades e comportamento malicioso.
   - **npq**: O `npq` é uma ferramenta que verifica pacotes em busca de sinais de alerta, como números anormais de downloads e depreciações.

### 7. **Verifique Metadados do Pacote**
   - Cheque as informações do pacote no site do NPM (como autor, e-mail, licença, e versão).
   - Verifique se o pacote foi publicado recentemente e por um autor conhecido na comunidade.

### 8. **Busque Análises e Relatórios de Segurança**
   - Consulte sites como [npm registry advisories](https://www.npmjs.com/advisories) e [Snyk](https://snyk.io/vuln) para ver se há alertas de segurança para o pacote.

### 9. **Revise Permissões de Acesso**
   - Evite instalar pacotes com permissões excessivas, como permissões de leitura/gravação fora do diretório do projeto.
   - Desconfie de pacotes que requerem acesso a variáveis de ambiente sensíveis, como `process.env`.

### 10. **Use Instalação Segura**
   - Ao instalar pacotes, utilize a flag `--ignore-scripts` para evitar a execução de scripts durante a instalação:
     ```bash
     npm install <package> --ignore-scripts
     ```
   - Isso impede que scripts de ciclo de vida (`preinstall`, `postinstall`, etc.) sejam executados sem uma análise prévia.

Seguindo esses passos, você pode reduzir o risco de introduzir pacotes maliciosos em seu ambiente e manter seu projeto mais seguro.
