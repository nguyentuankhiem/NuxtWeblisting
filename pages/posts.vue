<template>
    <body>
        <ul>
            <li v-for="item in posts" :key="item.id">
                {{ item.gallery[0] }}
            </li>
        </ul>
    </body>
</template>


<script>
    import gql from "graphql-tag"
    export default {
        apollo: {
            posts: gql`query GetPost {
                posts(where: 
                {
                    pageInfor: 
                    {
                        slug: 
                        {
                            eq: "can-ho-the-sun-avenue-3pn2wc-tang-17-thoai-mai-sang-trong-40072"
                        }
                    }
                })
                {
                    id
                    pageInfor 
                    {
                        title
                        slug
                    }
                    status
                    gallery
                }
            
            }`
        }
    }
</script>