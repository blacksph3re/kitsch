# Kitsch kooking app

This is a unification of two cooking apps, done by Anja, Hendrik and Nico. The purpose is to accomodate a recipe recommendation algorithm and the price planning functionality of alastair in one, multi-functional cooking app.

It consists of several repositories, thus when cloning use the recursive flag.

* **[Loginservice](github.com/blacksph3re/loginservice)** Handling sign-on, login and basic user-related matters
* **[Alastair](github.com/blacksph3re/alastair2)** A recipe db originally designed to facilitate price calculations for event-cooking
* **Anja's part** Generating recommendations based on a set of input ingredients
* **[Frontend](https://github.com/t0m0ffel/kitsch-frontend/)** A frontend for all of the above written in Vue.js
* **[Kitsch](github.com/blacksph3re/kitsch)** A repo uniting all of the above, managing orchestration and deployment

## Usage

The kitsch.sh is a wrapper around docker-compose, automatically feeding in all the enabled services to the compose command. It can be used with the same syntax as the plain docker-compose command.

    # Starts everything
    sh kitsch.sh up -d

    # Inspect a container
    sh kitsch.sh logs -f kitsch-frontend

    # Run something in a running container
    sh kitsch.sh exec kitsch-frontend ash

    # Run something seperately without needing to start the whole system
    sh kitsch.sh run loginservice mix test

    # Stop everything, if given the -v switch also reset all db states
    sh kitsch.sh down -v