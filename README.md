# Pokédex em Drupal

Este projeto é uma Pokédex criada usando o CMS Drupal, MySQL e rodando em um ambiente Linux com WSL (Windows Subsystem for Linux). O objetivo deste projeto é fornecer uma base de dados de Pokémon com informações detalhadas sobre cada um deles, utilizando as funcionalidades e extensibilidade do Drupal.

## Descrição do Projeto

A Pokédex em Drupal é um aplicativo web que permite aos usuários navegar por uma lista de Pokémon, visualizar detalhes específicos de cada um, e realizar buscas e filtros avançados. Este projeto serve como uma demonstração das capacidades do Drupal para gerenciar conteúdos complexos e integrar dados externos.

## Funcionalidades

- **Listagem de Pokémon**: Exibição de uma lista de Pokémon com informações básicas.
- **Detalhes do Pokémon**: Visualização de informações detalhadas sobre cada Pokémon, incluindo tipo, habilidades, estatísticas e descrição.
- **Busca e Filtro**: Funcionalidades de busca e filtro para encontrar Pokémon específicos por nome, tipo, ou outras características.
- **Administração**: Interface de administração para gerenciar o conteúdo da Pokédex, adicionar novos Pokémon, e atualizar informações existentes.

### Implementação Futura:
- **Integração com API**: Capacidade de integrar com APIs externas para obter informações atualizadas sobre Pokémon.

## Estrutura do Projeto

A estrutura principal do projeto é organizada da seguinte forma:
```sql
pokedex-drupal/
├── modules/
│ ├── custom/
│ │ └── pokedex_module/
│ │ ├── src/
│ │ ├── templates/
│ │ ├── pokedex_module.info.yml
│ │ └── pokedex_module.module
├── themes/
│ ├── custom/
│ │ └── pokedex_theme/
│ │ ├── css/
│ │ ├── js/
│ │ ├── templates/
│ │ └── pokedex_theme.info.yml
├── sites/
│ ├── default/
│ │ ├── settings.php
│ │ └── files/
├── vendor/
├── .htaccess
├── composer.json
└── index.php
```



## Tecnologias Utilizadas

- **Drupal**: CMS utilizado para gerenciar e exibir os conteúdos da Pokédex.
- **MySQL**: Banco de dados relacional utilizado para armazenar as informações dos Pokémon.
- **PHP**: Linguagem de programação utilizada pelo Drupal.
- **Linux com WSL**: Ambiente de desenvolvimento e execução do projeto.
- **Composer**: Gerenciador de dependências para PHP.
- **Drush**: Ferramenta de linha de comando para administração do Drupal.
- **Twig**: Motor de templates utilizado pelo Drupal para renderizar páginas.
- **HTML/CSS/JavaScript**: Tecnologias de frontend para estilização e interatividade.

## Instalação e Configuração

### Pré-requisitos

- **WSL**: Instale o WSL e configure uma distribuição Linux (Ubuntu recomendado).
- **PHP**: Versão 7.4 ou superior.
- **MySQL**: Servidor MySQL instalado e rodando.
- **Composer**: Instalado globalmente.
- **Drush**: Instalado globalmente.

### Passos de Instalação

1. **Clone o Repositório**

 ```bash
 git clone https://github.com/seu-usuario/pokedex-drupal.git
 cd pokedex-drupal
 ```

```bash
composer install
 ```

### Configuração do Banco de Dados

Crie um banco de dados MySQL e configure as credenciais no arquivo settings.php:

```sql
CREATE DATABASE pokedex;
CREATE USER 'pokedex_user'@'localhost' IDENTIFIED BY 'senha_segura';
GRANT ALL PRIVILEGES ON pokedex.* TO 'pokedex_user'@'localhost';
FLUSH PRIVILEGES;
```

Configure o arquivo sites/default/settings.php:

```sql
$databases['default']['default'] = array (
  'database' => 'pokedex',
  'username' => 'pokedex_user',
  'password' => 'senha_segura',
  'host' => 'localhost',
  'port' => '',
  'driver' => 'mysql',
  'prefix' => '',
);
```

### Instale o Drupal

Execute o comando Drush para instalar o site Drupal:
```bash
drush site:install --db-url=mysql://pokedex_user:senha_segura@localhost/pokedex
Habilite o Módulo Customizado
```

Habilite o módulo da Pokédex:

```bash
drush en pokedex_module -y
```
### Uso
Acesse a instalação do Drupal através do navegador web:
http://localhost:8080
