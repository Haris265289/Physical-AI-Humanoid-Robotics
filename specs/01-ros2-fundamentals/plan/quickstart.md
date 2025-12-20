# Quickstart Guide: ROS 2 Fundamentals Module

## Overview
This guide will help you set up the Docusaurus-based textbook for the ROS 2 Fundamentals module. Follow these steps to get the development environment running and create the initial content structure.

## Prerequisites
- Node.js (version 18 or higher)
- npm or yarn package manager
- Git for version control
- Basic familiarity with command line tools

## Step 1: Initialize Docusaurus Project

1. **Create a new Docusaurus project**:
   ```bash
   npx create-docusaurus@latest textbook-website classic
   cd textbook-website
   ```

2. **Install additional dependencies**:
   ```bash
   npm install @docusaurus/module-type-aliases @docusaurus/types
   ```

3. **Verify the installation**:
   ```bash
   npm start
   ```
   You should see the default Docusaurus site running on http://localhost:3000

## Step 2: Configure Project Structure

1. **Create the modules directory structure**:
   ```bash
   mkdir -p docs/modules/01-ros2-fundamentals
   ```

2. **Create the three chapter files**:
   ```bash
   touch docs/modules/01-ros2-fundamentals/01-ros2-architecture.mdx
   touch docs/modules/01-ros2-fundamentals/02-rclpy-control.mdx
   touch docs/modules/01-ros2-fundamentals/03-urdf-modeling.mdx
   ```

## Step 3: Configure Navigation

1. **Update the sidebar configuration** in `sidebars.js`:
   ```javascript
   module.exports = {
     textbook: [
       {
         type: 'category',
         label: 'Module 1: The Robotic Nervous System (ROS 2)',
         items: [
           'modules/01-ros2-fundamentals/01-ros2-architecture',
           'modules/01-ros2-fundamentals/02-rclpy-control',
           'modules/01-ros2-fundamentals/03-urdf-modeling'
         ],
       }
     ]
   };
   ```

2. **Update the main configuration** in `docusaurus.config.js` to reflect the textbook nature:
   ```javascript
   // Add or update these sections in your docusaurus.config.js
   module.exports = {
     title: 'Physical AI & Humanoid Robotics Textbook',
     tagline: 'An AI-Native Textbook with RAG Chatbot',
     // ... other config
     presets: [
       [
         'classic',
         /** @type {import('@docusaurus/preset-classic').Options} */
         ({
           docs: {
             sidebarPath: require.resolve('./sidebars.js'),
             editUrl: 'https://github.com/your-org/your-repo/edit/main/',
           },
           // ... other preset config
         }),
       ],
     ],
     // ... rest of config
   };
   ```

## Step 4: Add Initial Content to Chapters

1. **Edit the ROS 2 Architecture chapter** (`docs/modules/01-ros2-fundamentals/01-ros2-architecture.mdx`):
   ```md
   # Introduction to ROS 2 Architecture

   Welcome to Module 1 of the Physical AI & Humanoid Robotics Textbook. In this chapter, you'll learn about the fundamental architecture of ROS 2 and how it serves as the nervous system for humanoid robots.

   ## Learning Objectives
   - Understand the role of ROS 2 in Physical AI systems
   - Learn about nodes, topics, services, and actions
   - Explore the DDS-based communication model

   ## What is ROS 2?
   ROS 2 (Robot Operating System 2) is not an operating system but rather a collection of tools, libraries, and conventions that aim to simplify the task of creating complex and robust robot behavior across a wide variety of robot platforms and environments.

   [Continue with detailed content...]
   ```

2. **Edit the rclpy Control chapter** (`docs/modules/01-ros2-fundamentals/02-rclpy-control.mdx`):
   ```md
   # ROS 2 Programming with Python (rclpy)

   In this chapter, you'll learn how to write ROS 2 nodes in Python using the rclpy client library.

   ## Learning Objectives
   - Write ROS 2 nodes in Python
   - Implement publisher-subscriber patterns
   - Create service and action-based control for robots

   ## Setting Up rclpy
   The rclpy package is the Python client library for ROS 2. It provides the tools you need to create ROS 2 nodes, publish and subscribe to topics, and provide and use services.

   [Continue with detailed content...]
   ```

3. **Edit the URDF Modeling chapter** (`docs/modules/01-ros2-fundamentals/03-urdf-modeling.mdx`):
   ```md
   # Robot Modeling with URDF

   This chapter covers the Unified Robot Description Format (URDF) and how to model humanoid robots for use with ROS 2.

   ## Learning Objectives
   - Understand the purpose of URDF in humanoid robotics
   - Define links, joints, and sensors in URDF
   - Integrate URDF models with ROS 2 simulations

   ## What is URDF?
   URDF (Unified Robot Description Format) is an XML format used to model robot geometry, kinematics, and dynamics in ROS. It allows you to describe a robot in terms of its links (rigid parts) and joints (connections between links).

   [Continue with detailed content...]
   ```

## Step 5: Run and Test

1. **Start the development server**:
   ```bash
   npm start
   ```

2. **Verify the navigation**:
   - Check that the Module 1 category appears in the sidebar
   - Verify that all three chapters are accessible
   - Test that links work correctly

3. **Check the content**:
   - Navigate to each chapter and verify the content displays correctly
   - Ensure proper formatting and styling

## Step 6: Deployment Preparation

1. **Build the static site**:
   ```bash
   npm run build
   ```

2. **Test the production build locally**:
   ```bash
   npm run serve
   ```

3. **Prepare for GitHub Pages deployment**:
   - Configure the `deployment` section in `docusaurus.config.js`
   - Set up GitHub Actions for automatic deployment (optional)

## Troubleshooting

### Common Issues

**Issue**: Sidebar navigation not showing up
**Solution**: Verify that the `sidebars.js` file is correctly formatted and that all document IDs match the file paths

**Issue**: Content not displaying properly
**Solution**: Check that MDX files have proper frontmatter and that all referenced components are properly imported

**Issue**: Local development server not starting
**Solution**: Clear npm cache (`npm cache clean --force`) and reinstall dependencies (`npm install`)

### Performance Tips

- Use code splitting for large examples
- Optimize images and media files
- Use Docusaurus' built-in MDX features efficiently
- Implement proper lazy loading for interactive components

## Next Steps

After completing this quickstart:
1. Add detailed content to each chapter based on the specification
2. Include practical examples and exercises
3. Implement interactive elements where appropriate
4. Set up the RAG system to index the content
5. Test the chatbot integration with the textbook content