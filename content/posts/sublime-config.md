---
title: "Configuração: Sublime Text 4"
slug: "Configuração: Sublime Text 4"
date: 2022-12-29
draft: false
tags:
- teste
categories: 
- Epopéias
---

Esta pode ser a primeira publicação da série **epopéias**, que narram as configurações para diversos softwares. Essa epopéia trata da configuração do **SublimeText 4**.

&nbsp;

Antes de iniciar, vale destacar as características do sistema e restrições que enfrentei.

- Utilizo o Zeron OS Pro 16.1, baseado no Ubuntu 20.04;

- Utilizo o Sublime Text 4;

- Utilizo o Chrome(latest) instalado através do Flatpak;

&nbsp;

Para que o código html seja exibido em um determinado navegador (instalado através do Flatpak, que infere uma série de restrições), realizei a seguinte configuração:

&nbsp;

1. Personalizei a opção de Build System. Menu superior > Build System > New build system;

   ```
   {
   	"cmd":["/var/lib/flatpak/exports/bin/com.google.Chrome","$file"]
   }
   ```

2. Salvei o arquivo com Chrome (Chrome.sublime-build);

3. Instalei a aplicação **Flatseal**, que facilita a configuração de permissões em softwares instalados através do Flatpak;

4. Adicionei a configuração abaixo (caminho relativo a partir de minha home) ao Chrome¹. Para consultar outras permissões, [acesse a documentação do Flatpak](https://docs.flatpak.org/en/latest/sandbox-permissions-reference.html).

   ```
   --filesystem=~/meudiretoriohtml
   ```

   

5. Fechei e reabri o Sublime Text 4 e o Chrome;

6. Criei um código html qualquer dentro do diretório acima e pressionei ctrl+b para construir².

&nbsp;

&nbsp;

¹ Para facilitar a configuração de permissões em aplicações do Flatpak, instalei o Flatseal.

² Comando Build.



