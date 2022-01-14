<template>
    <html>
        <body>
            <ul>
                <li v-for="item in posts" :key="item.id">
                    {{ item.pageInfor.slug }}
                </li>
            </ul>
        </body>
    </html>
</template>


<script>
    import gql from "graphql-tag"
    export default {
        apollo: {
            posts: gql`query GetPost {
                posts
                {
                    id
                    pageInfor 
                    {
                        title
                        slug
                    }
                    status
                }
            
            }`
        }
    }
</script>