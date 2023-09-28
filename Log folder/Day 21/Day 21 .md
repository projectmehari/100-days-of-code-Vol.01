# Day 21

Tags: User Research
Date: December 10, 2022
Status: Done

Tasks of the day

- ****[Learn Design Thinking: Ideation](https://www.codecademy.com/learn/learn-design-thinking-ideation)****
- ****[Music NFT metadata w/ Zora API and Python Pandas - Ahmed Alkarboly](https://www.youtube.com/watch?v=fA5wnKy201c)****

---

This document covers various ideation techniques, including Worst Possible Idea, Brainwriting, Crazy 8's, Mind Mapping, and SCAMPER. It also provides best practices for brainstorming and mind mapping, as well as tips for concept testing and creating a UX case study. The document emphasizes the importance of iteration and documentation throughout the design thinking process.

## ****Music NFT metadata w/ Zora API and Python Pandas - Ahmed Alkarboly****

**Underground violet rave**

Zora API overview

![Screen Shot 2022-12-10 at 4.45.47 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.45.47_PM.png)

GraphQL

- Explore panel
- Realtime view panel
- Execution panel

![Screen Shot 2022-12-10 at 4.48.36 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.48.36_PM.png)

- We can use the API to return all the semi-structured (JSON) data for a particular publishing platform (MintSongs, Catalog, Sound.xyz, etc) or independent artist.
- Music spread out across different collections is not scalable
- Music NFT metadata standard adoption is key for easy integration into micro-service ecosystems.
- Data aggregation is needed to make services possible

![Screen Shot 2022-12-10 at 4.49.41 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.49.41_PM.png)

![Screen Shot 2022-12-10 at 4.50.03 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.50.03_PM.png)

![Screen Shot 2022-12-10 at 4.50.31 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.50.31_PM.png)

![Screen Shot 2022-12-10 at 4.51.10 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.51.10_PM.png)

Pandas Walkthrough - Prerequisites

- Code editor (I used VS code)
- Python + libraries installed
- Google Cloud API credentials (If you want to store data on the cloud)

![Screen Shot 2022-12-10 at 4.53.51 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_4.53.51_PM.png)

- **Import and clients**
- **Define data frame and initiate variables**
- **Dynamic Query** ( Count pages processed, execute query on first page of collection if first page, Execute query on next page of collection if not first page)
- **Execute Query** ( Initiate query, execute query, return JSON node page, load into a dataframe and then create a node page)
- **Grabbing the metadata** (Iterate through each song on node page, assign variable value by navigating JSON file to return specified data)
- 

That’s how you build a music NFT metadata aggregator built on the Zora API

![Screen Shot 2022-12-10 at 5.05.44 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_5.05.44_PM.png)

### What can we start to do with metadata aggregation?

- Music charting
- Playlisting
- Music discovery
- IP and music rights automation
- Ecosystem analysis
- Music players

![Screen Shot 2022-12-10 at 5.09.21 PM.png](Day%2021%20af212e28bd574778a3986afe296b114a/Screen_Shot_2022-12-10_at_5.09.21_PM.png)

### What I did with my integration

- Curated and DJ’d a set using NFT metadata
- You can listen to it here
- Github code here

---

### Design thinking Ideation

**Define and ideate**

The [design thinking](https://www.codecademy.com/resources/docs/uiux/design-thinking) process asks us to place the user at the center of our work. Implementing a user-centered approach may feel quite natural during the “empathize” stage. After all, in our efforts to understand users, we conduct research that often brings us face-to-face. We may meet in person, have a discussion via phone or video chat, or gather written responses that reveal their unique opinions, frustrations, and goals.

**Define and ideate with empathy**

After conducting generative user research, we are equipped to define a real problem that users are experiencing. Then, with this user-centered problem in mind, we can ideate relevant solutions.

How can designers keep the user at the center of the “define” and “ideate” stages

- Designers should ise insights from user research to guide how they define a problem and how they intend to solve it.

### Ideate

In the **ideate stage**, we explore solutions to a defined problem. At this time, we aren’t trying to find the perfect solution. Instead, we use our creative energy to generate a towering heap of ideas. With a wide range of ideas at our disposal, we can ultimately select the ones that offer the most promising solutions for the problem that users are experiencing.

### Purpose

The define stage has us identify *what* problem we are trying to solve, and the ideate stage prompts us to consider *how*. When we start ideating, we consider many different possibilities, even if they seem strange, implausible, or downright bad (There’s a brainstorming technique dedicated to bad ideas, aptly named [Worst Possible Idea](https://www.interaction-design.org/literature/topics/worst-possible-idea#:~:text=Worst%20Possible%20Idea%20is%20an,gain%20insights%20towards%20great%20ideas)!). We’re aiming for a large number of ideas, so we don’t need to worry about quality just yet.

### Application

When picking an ideation strategy, consider the context of your project. Certain techniques may be more effective for team settings, while others can be easily applied if you are working alone. You might also consider whether you’ll work with digital tools, pen and paper, or a mix of both. Lastly, you don’t need to limit yourself to one method! Mixing and matching can be helpful, as different techniques lead us to access different types of thinking.

Here are a few ideation techniques that may be useful:

- [Brainwriting](https://www.smashingmagazine.com/2013/12/using-brainwriting-for-rapid-idea-generation/)
- [Crazy 8’s](https://designsprintkit.withgoogle.com/methodology/phase3-sketch/crazy-8s)
- [Mind Mapping](https://careerfoundry.com/en/blog/ux-design/design-thinking-exercises/#mind-mapping)
- [S.C.A.M.P.E.R.](https://www.mindtools.com/pages/article/newCT_02.htm)
- [Worst Possible Idea](https://www.interaction-design.org/literature/topics/worst-possible-idea#:~:text=Worst%20Possible%20Idea%20is%20an,gain%20insights%20towards%20great%20ideas.)

**Digital tools:** The following tools are digital whiteboards. Team members can view and edit the same board, and they have access to features like sticky notes, comments, shapes, text, templates, and other tools that aid collaborative ideation.

- Miro
- Figjam
- Jamboard

Physical Tools: If you’re working in person, you want to make sure everyone can record their ideas and share them with the team.

- Paper and pens
- Sticky notes
- Whiteboard and marker

### What’s next?

During the ideation stage, we will generate more ideas than we could possibly pursue with one design.

There are many strategies for selecting the ideas, including:

- [Dot Voting](https://www.nngroup.com/articles/dot-voting/)
- [Cost-Benefit Analysis](https://www.mindtools.com/pages/article/newTED_08.htm)
- [Four Categories](https://www.interaction-design.org/literature/article/stage-3-in-the-design-thinking-process-ideate)
- [Wow Now How Matrix](https://www.sessionlab.com/methods/how-now-wow-matrix)

**What is a standard outcome of the ideate stage?**

- A wide range of possible solutions that address a defined problem

### Brainstorm

Brainstorming is the process of generating several ideas based on a central topic or question. It’s a popular, flexible ideation method that is applied in many contexts.

### Best practices

A productive brainstorming session calls us to balance free-thinking and focus. Free-thinking is essential because we don’t want to limit our ideas. At this moment, we’re not concerned about identifying surefire solutions. We should feel inspired to toss out every idea we can imagine, even if they are outlandish or undeveloped.

To encourage free-thinking:

- Avoid placing judgment (good or bad) on an idea
- Combine and iterate on ideas in the moment
- Use different methods (speaking, writing, sketching) to unlock different types of thinking
- Set a time limit to emphasize speed over depth

### Mind mapping

Mind mapping is a brainstorming technique that helps us transform one general concept into several specific, actionable ideas. As we expand our map, each new idea may spark dozens more. By the end of the activity, we have a wide variety of solutions and a visual record of our thought process.

Mind mapping is a flexible activity that can be customized to suit various contexts in the design world and beyond. This technique can be facilitated in-person or online and you can work individually or with a team. We’ll walk through a version that is conducive to our goals in this lesson.

1. To start, we add a topic to the middle of the page and draw a circle around it. For a design project, we could use a problem statement or a question based on the problem statement.
2. Next, we draw a few lines stemming from the central circle. We;ll call these our primary branches. At the end of each primary branch, we add a broad solution or an aspect of the problem to explore. For example, if our central question is “how might we connect people who share common hobbies?, then could add”local events”, “volunteer opportunities”, and “online meetups”
3. From this point, we pick a solution from a primary branch and add some lines around it. At the end of these secondary branches, we imagine ways to execute the solution. We can still use short phrases, but these ideas should be more concrete and specific. If a potential solution is “online meetups”, we could propose ideas like: “hobby-specific social media site”, notifications about online events related hobby” and “skill-sharing app focused on collaboration and relationships.”

### Four categories

 [Four Categories](https://www.interaction-design.org/literature/article/stage-3-in-the-design-thinking-process-ideate) is a method developed by the [Interaction Design Foundation](https://www.interaction-design.org/)
 for deciding which ideas to move forward with after a brainstorm.

We start with four predetermined categoes:

- **Most rational**: solutions that we can efficiently and effectively develop with the given time and resources.
- **Most delightful:** solutions that users may find most appealing and exciting
- **Darling**: solutions that we feel passionate about
- **Long shot:** solutions that do not seem feasible. These ideas might be expensive, complex, or seemingly impossible to pull off. We might feel less confident about how users will react to these solutions.

### **Sketch**

During the ideation process, it can be helpful to create visual representations of our ideas. One go-to method for creating these visuals is to sketch them.

**Sketching** is the process of quickly drafting a rough visual that serves as a thinking or communication tool.

The goal is to generate an image that supports our thinking, such as clarifying a concept, mapping a process, or documenting a thought.

### Sketch vs Wireframe

A notable difference between sketches and wireframes is how we approach them. We should spend less time and effort on sketches than wireframes. When sketching, we establish a general picture without including too much detail. Sketches are always [low-fidelity](https://www.codecademy.com/resources/docs/uiux/low-fidelity) whereas wireframes can be rendered in various fidelities. As long as we get the idea across, we have created a successful sketch!

### When and how to sketch

Like brainstorming, sketching is not confined to a specific stage in the design thinking process. We can sketch whenever it aids our work. That being said, sketching can be especially useful during the “ideate” stage.

### Iterate

**Iteration** is the practice of revising ideas based on new insights or feedback from team members. While iteration is an activity we can complete, it is also a mindset we can embrace.

By embracing an iterative mindset, we expect and accept change. This mindset helps us be receptive to continually adjusting a design, instead of getting attached to solutions that ultimately aren’t viable. An iterative mindset can even boost creativity as we build the habit of exploring multiple ideas and revising them.

**Why iterate**

We must continuously adapt our ideas to align with new information, so the design reflects our current knowledge. By iterating, we fix errors, address assumptions, incorporate feedback, and transform good designs into great ones.

**Define, ideate, iterate**

Iteration is inseparable from the “ideation” stage. While brainstorming, we produce an array of ideas and spontaneously iterate on ideas as they emerge. When we sketch, we can produce iterations that demonstrate different possibilities based on the same idea. Also, we can iterate on brainstormed ideas and sketches after gaining new information from concept testing, prototyping, or usability testing.

**Document**

The process of saving iterations and other artifacts is called **documentation**. We can document paper artifacts by labeling them and arranging them in a folder or drawer. In some cases, we might want to digitize these papers by scanning or photographing them and uploading them to a device.

**What does iteration look like during the design thinking process?**

- Adjusting and improving the design based on feedback from users or stakeholders.

### Concept test

**Concept testing** is a user research method that’s mostly used in marketing and product design.

The goal of a concept test is to get user feedback before investing time and resources in developing an idea more fully. We think of a concept test as a traffic light. Based on the test results, we might go forward with an idea, slow down to revise it, or stop pursuing the idea altogether.

**Purpose**

Concept testing gives us the opportunity to directly connect with users at a pivotal point in the design process. We can empathize with users when they are not in the room with us, but it is also valuable to learn exactly what they are thinking.

Running a concept test can help us:

- Validate an idea or determine if it is not viable.
- Save resources by gathering user feedback early on
- Address assumptions that were made in the solution or problem statement
- Spark data-backed iterations and uncover alternative solutions
- Clarify how the design can actually meet user needs.

After developing a prototype, we run a [usability test](https://www.nngroup.com/articles/usability-testing-101/) to observe how users experience a design. By contrast, the concept test helps us understand which design ideas might be most valuable for users.

### Timing

The “when” and “how” of concept testing will vary for each project, but we can always start by outlining our goals. Once we decide what we want to learn, we can determine how to run a concept test that will fetch the desired insights.

### Methods

If you have studied [user research](https://www.codecademy.com/resources/docs/uiux/user-research), the methods for concept testing may be familiar. Common methods include surveys, interviews, focus groups, and A/B testing. In a concept test, we borrow familiar research structures and tailor them to fit our goals.

- Do we need quantitative data, qualitative data, or both?
- What can users tell us that we can’t learn from other sources?
- How will we measure and evaluate users responses? Do we need a certain number to react positvely in order to move forward with an idea?

### Concept test interview

Here’s how we could set up our concept test interview:

1. **Set a research goal**: Describe what you want to learn from this concept test.
2. **Create a research question:** The research goal describes the intented outcome, and the research question gives you a starting point. You will achieve the research goal by seeking answers to the research question. (The research question can be broad. In the interview, you will ask specific questions based on this broad question.)
3. **Create an interview script:** Decide how you will explain the concept. Create or select artifacts that can help clarify the concept. Include enough context so that participants know how the concept will work.
4. **Write open-ended interview questions:** Each interview question will explore a specific aspect of the research question. Make sure that the questions don’t reflect your personal biases or lead the participants to answer in a specific way.
5. **Get feedback**: Test your script and artifact on a team member or two. This can help you work out any glaring issues before speaking to participants.
6. **Identify relevant participants**: The participants should be potential users of the design. If the participants have no use for the concept, it will be difficult for them to provide relevant feedback. Review previous user research to identify key characteristics of your users.
7. **Schedule and facilate the interview:**  Be curious and open-minded — don’t approach the session with a set idea about how users will respond. Ask follow-up questions to investigate why participants feel the way that they do. If you’re testing multiple concepts, swap the order of the concept for each session. This mitigates the possibility that participants favor a certain option simply because it was presented first.

### Now what?

After analyzing the results of a concept test, we could:

- Combine ideas that appealed to users for different reasons
- Iterate on an idea to better align it to user needs
- Create a prototype based on an idea that users responded positively to
- Set aside an idea that is misaligned with user needs
- Refine the problem statement to better match user needs

What is the goal of concept testing?

- Concept testing helps designers make user-centered decisions about whether to revise, pursue , or reject early design ideas.

### Learn design thinking: Ideation

**Connect best: define and ideate**

Now, you will use this research to define a problem that users are experiencing. Then, you will ideate many possible solutions to the problem. Lastly, you will gain feedback about your top two ideas and use that feedback to spark some iterations.

In this project, you will focus on activities that are associated with the “define” and “ideate” stages of the design thinking process:

- Define a problem based on user research
- Brainstorm many possible solutions
- Sort ideas and select two to explore
- Sketch your top two ideas
- Obtain feedback about your top two ideas

### Set up the project

1. Follow the instructions on the website to the right to duplicate the project template Miro board.
2. Click the “Open Boards Picker” button (you may need to scroll down). Select “Copy of Connect Best: Define and Ideate” to embed the board.

### Define

1. Review the research report you created for the [Research Report Project](https://www.codecademy.com/courses/learn-user-research-generative/projects/ui-and-ux-connect-best-research-report) or review the sample research report.
2. Answer the 5 W’s based on the research report you’re using.
3. Write a problem statement (2-4 sentences) that is based on your responses to the 5 W’s.

### Ideate

1. Create a mind map to brainstorm many possible solutions to the problem you have defined.
2. Using the [Four Categories](https://www.interaction-design.org/literature/article/stage-3-in-the-design-thinking-process-ideate) method, sort the ideas from your mind map into categories.
3. Review your Four Categories chart and highlight your top two ideas with a bright color. If possible, select ideas from different categories.
4. On paper or in Miro, create sketches of your top two ideas.
5. Document your sketches so you can readily access them later on.

### Get Feedback

1. Read the information in this task to gain context for the “Get Feedback” section of the project.
2. Read the feedback session script. Fill in the blanks to customize the script for your project.
3. Customize the feedback session invitation. Send the invitation to one participant to schedule a feedback session.
4. Facilitate a feedback session with one participant.

### Reflect

1. Reflect on the feedback session. Consider how you could iterate on the concepts based on the feedback.
2. Now that you have completed the project, take a look at our example to see how we approached the ideation process

## What is a UX case study?

A case study is a start-to-finish walkthrough of the process of completing a project, telling the story of how a given design project was brought to fruition.

**A strong case study might include:**

- **Summary**: A quick summary of what type of project this was and what was achieved, which viewers can understand at a glance and decide whether to dig deeper into the case study. For example: “Research-driven redesign of a mobile travel app leading to 50% improvement in user retention.”
- **Goal or problem statement**: What was the issue or goal you set out to solve? What was the team trying to achieve?
- **Team and role**: Who was on the team working on this project, and what was your specific role?
- **Tools used**: What software or other tools were used to complete this project?
- **Timeline**: How long did the project take from start to finish?
- **Process**: An overview of the start-to-finish process that the team embarked on. Here, you might share process documentation such as your visual style guide or different design options or iterations.
- **Results or findings**: What were the primary solutions you and your team offered? For a design project, this might look like various design deliverables. For a research-heavy project, this might include key research findings.

### Tips for writing case studies

A case study can be thought of like any story: Start with a problem, and end with a resolution, in which you and your team were the hero. What kind of growth and lessons were learned along the way? What challenges or tension did you encounter and solve, and how?

Most UX case studies today live online in the designer’s web portfolio. In some cases, you might additionally format your case studies and portfolio as a PDF or slide deck that can be downloaded or printed to share during interviews.

### Selecting Case study projects

Try to put yourself in the position of the target user. Imagine you’re a hiring manager: What questions are you looking to have answered? How can you, as a designer, answer some of those questions upfront and make it clear that you’re the best pick for the job?

If you’re open to different types of work, you may want to consider case studies that highlight your different strengths. For example, you might feature a UX design project focused on wireframes alongside a user research project where the primary outcome was a research report. 4 to 5 case studies maximum is a good rule of thumb.

- **Create speculative projects**: for example, choose a problem you care about and design a product to address the pain points, or choose a website you think could be designed better and create your own case study of a redesign. (Just be sure to make it clear that the project was personal/speculative and you were not actually hired by the company to work on this project.)
- **Take educational courses**: Consider online courses (like this one!), in-person courses, or bootcamps that include portfolio projects. If you plan to use a project for a case study, treat it like you would a real professional project and invest time and creativity into the project. Take the opportunity to show off your strongest skills.
- **Seek out freelance projects**: Consider finding freelance projects through websites like [Dribbble](https://dribbble.com/freelance-jobs) or [Upwork](https://www.upwork.com/), or through your personal networks.
- **Volunteer your skills**: Consider volunteering your skills for a good cause. In general, designers should be wary of working for free, but doing so for a nonprofit or community organization could be mutually beneficial and buff out your portfolio.

### Documenting your design work

Document each step of the design process as you work. For example, take a photo of your whiteboard or sticky notes from a planning session, save your site map and information architecture planning documents, scan your paper prototypes, and preserve each design iteration in your [design software](https://www.codecademy.com/resources/docs/uiux/design-software) (i.e. Figma or Adobe XD), from [low fidelity](https://www.codecademy.com/resources/docs/uiux/low-fidelity) all the way to [high-fidelity](https://www.codecademy.com/resources/docs/uiux/high-fidelity). Visuals from every step of the process help illustrate your thinking and make your case studies easy for a reader to skim through.