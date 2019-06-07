<template>
    <div class="app">
        <header class="app-header header">
            <Hero />
        </header>

        <div class="app-container container-fluid">
            <div class="row">
                <div class="app-sidebar col-md-3 d-none d-md-block ">
                    <SideBar :answers="fetchedData" class="menu sticky-top" />
                </div>

                <Main :answers="fetchedData" class="app-main col main" />
            </div>
        </div>

        <div class="app-footer footer">
            <Footer />
        </div>
    </div>
</template>

<script>
    import axios from "~/plugins/axios"
    import Hero from "~/components/Header/Hero.vue"
    import SideBar from "~/components/SideBar.vue"
    import Footer from "~/components/Footer.vue"
    import Main from "~/components/Main.vue"

    export default {
        components: {
            Hero,
            SideBar,
            Main,
            Footer
        },

        // asyncData() {
        //     return axios.get("/api/survey").then(({ data }) => {
        //         return { fetchedData: data }
        //     })
        // }
        data(){
            return {
                fetchedData:[
                    {
                        "name": "application_server",
                        "value": {
                            "1": 5,
                            "a": 10,
                            "d": 10,
                            "Puma": 10,
                            "Unicorn": 10,
                            "b": 5,
                            "c": 5,
                            "e": 5,
                            "f": 5,
                            "g": 5,
                            "h": 5,
                            "sad": 5,
                            "asd": 5,
                            "as": 5,
                            "w": 5,
                            "x": 5
                        }
                    },
                    {
                        "name": "server_os",
                        "value": {
                            "Ubuntu": 25,
                            "Windows Server": 25,
                            "Debian": 25,
                            "CentOS": 25
                        }
                    },
                    {
                        "name": "deploy_tools",
                        "value": {
                            "CircleCI": 50,
                            "Jenkins": 25,
                            "GitlabCI": 25
                        }
                    },
                    {
                        "name": "proxy_server",
                        "value": {
                            "Nginx": 40,
                            "Traefik": 20,
                            "Elastic Load Balancing": 20,
                            "Apache": 20
                        }
                    },
                    {
                        "name": "program_language",
                        "value": {
                            "Ruby": 25,
                            "Java": 25,
                            "PHP": 25,
                            "JavaScript": 25
                        }
                    },
                    {
                        "name": "framework",
                        "value": {
                            "Express": 25,
                            "Sail": 25,
                            "Laravel": 25,
                            "Rail": 25
                        }
                    },
                    {
                        "name": "serivce",
                        "value": {
                            "S3": 33.3,
                            "AWS": 33.3,
                            "SN": 33.3
                        }
                    },
                    {
                        "name": "database_server",
                        "value": {
                            "a": 12.5,
                            "PostgreSQL": 6.3,
                            "MySQL": 6.3,
                            "Elasticsearch": 6.3,
                            "MongoDB": 6.3,
                            "Cassandra": 6.3,
                            "b": 6.3,
                            "c": 6.3,
                            "d": 6.3,
                            "e": 6.3,
                            "f": 6.3,
                            "g": 6.3,
                            "h": 6.3,
                            "v": 6.3,
                            "x": 6.3
                        }
                    },
                    {
                        "name": "other_tools",
                        "value": {
                            "Asana": 50,
                            "Redmine": 50
                        }
                    }
                ]
            }
        }
    }
</script>

<style lang="scss">
    .app {
        &-header {
            background-color: #000000;
            min-height: 300px;
            color: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        &-sidebar {
            background-color: #fff;
        }

        &-footer {
            background-color: rgb(241, 245, 250);
            min-height: 100px;
        }
    }
</style>
