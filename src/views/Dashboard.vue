<template>
  <div class="dashboard">
    <!-- Header -->
    <v-subheader class="py-0 d-flex justify-space-between rounded-lg">
      <h3 style="color: white">Dashboard</h3>
      <v-btn color="success"> View All Projects</v-btn>
    </v-subheader>
    <br />

    <!-- Main Content -->
    <v-row>
      <!-- Left Column: Project Summary -->
      <v-col lg="7" cols="12">
        <v-alert dense text type="success">
          Login Successfully! Welcome to <strong>Admin Console</strong>
        </v-alert>

        <!-- Project Statistics Cards -->
        <v-row>
          <v-col
            lg="6"
            cols="12"
            v-for="(item, index) in projectStats"
            :key="index"
          >
            <v-card elevation="2" class="rounded-lg">
              <v-card-text class="d-flex justify-space-between align-center">
                <div>
                  <strong>{{ item.title }}</strong> <br />
                  <span>Last 1 week</span>
                </div>
                <v-avatar
                  size="60"
                  :color="item.color"
                  style="border: 3px solid #444"
                >
                  <span style="color: white">{{ item.amount }}</span>
                </v-avatar>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>

      <!-- Right Column: Recent Activities -->
      <v-col cols="12" lg="5">
        <v-card>
          <v-card-title>Recent Activities</v-card-title>
          <v-card-text class="py-0">
            <v-timeline align-top dense>
              <v-timeline-item color="indigo" small>
                <strong>10 Minutes ago</strong>
                <div class="text-caption">New task added to Project Alpha</div>
              </v-timeline-item>
              <v-timeline-item color="green" small>
                <strong>30 Minutes ago</strong>
                <div class="text-caption mb-2">Project Beta was completed!</div>
              </v-timeline-item>
              <v-timeline-item color="indigo" small>
                <strong>50 Minutes ago</strong>
                <div class="text-caption">Team Meeting was concluded</div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-card>
      </v-col>

      <!-- Full Width Column: Recent Projects/Tasks -->
      <v-col cols="12">
        <v-card>
          <v-data-table
            caption="Recent Project List"
            :headers="projectHeaders"
            :items="projects"
            :items-per-page="5"
            class="elevation-1"
          >
            <template v-slot:item.action="{ item }">
              <v-btn
                color="success"
                outlined
                small
                shaped
                @click="viewProject(item)"
              >
                View
              </v-btn>
            </template>
          </v-data-table>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data() {
    return {
      // Project statistics for the dashboard
      projectStats: [
        {
          title: "Active Projects",
          amount: 12,
          color: "cyan lighten-3",
        },
        {
          title: "Completed Tasks",
          amount: 75,
          color: "green darken-2",
        },
        {
          title: "Pending Tasks",
          amount: 23,
          color: "blue-grey darken-1",
        },
        {
          title: "Overdue Tasks",
          amount: 5,
          color: "deep-orange darken-1",
        },
      ],

      // Headers for the projects/tasks table
      projectHeaders: [
        { text: "Project Name", value: "name" },
        { text: "Status", value: "status" },
        { text: "Deadline", value: "deadline" },
        { text: "Priority", value: "priority" },
        { text: "Actions", value: "action" },
      ],

      // Example project data
      projects: [
        {
          name: "Project Alpha",
          status: "In Progress",
          deadline: "2024-09-15",
          priority: "High",
        },
        {
          name: "Project Beta",
          status: "Completed",
          deadline: "2024-08-30",
          priority: "Medium",
        },
        {
          name: "Project Gamma",
          status: "Not Started",
          deadline: "2024-10-05",
          priority: "Low",
        },
        {
          name: "Project Delta",
          status: "In Progress",
          deadline: "2024-09-20",
          priority: "High",
        },
        {
          name: "Project Epsilon",
          status: "In Progress",
          deadline: "2024-09-25",
          priority: "Medium",
        },
      ],
    };
  },
  methods: {
    viewProject(item) {
      console.log("View details for " + item.name);
      // Implement project view logic, such as routing to a detailed project page
    },
  },
};
</script>

<style scoped>
/* Customize any additional styling if needed */
</style>
