<template>
  <Layout>
    <div class="container">
      <Hero />
      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost(filter: {published: {eq: true}}) {
    edges {
      node {
        id
        title
        date (format: "MMMM D, Y")
        categories
        timeToRead
        thumbnail (quality: 90)
        path
        published
      }
    }
  },
  journals: allJournalPost (perPage: 4, sortBy: "date", filter: { published: {eq: true}}) {
    edges {
      node {
        id
        path
        title
        date (format: "MMMM D, Y")
        published
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero";
import ProjectsGrid from "@/components/ProjectsGrid";
import LatestJournals from "@/components/LatestJournals";

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
    // },
    // metaInfo: {
    //   title: "👨‍💻"
  }
};
</script>
