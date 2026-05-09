You are my senior full-stack engineer and AWS solutions architect.

Build a production-style demo app called “BuilderHub AI”.

Context:
This demo is for a student talk titled “The Innovation Fast-Track: Building with Cursor & AWS”.
The goal is to show how students can move from “just coding” to shipping a real AI-powered community solution using Cursor and AWS.

App idea:
BuilderHub AI is an AI-powered community project platform for students and organizers.

Users should be able to:
1. View community projects.
2. Submit a new project idea.
3. Ask AI for feedback on a project.
4. Receive AI-generated suggestions for:
   - Better problem statement
   - Possible AWS architecture
   - Security risks
   - Cost-saving ideas
   - Next build steps
5. View a simple organizer dashboard showing project count, feedback count, and recent submissions.

Tech stack:
- Next.js 14+ with App Router
- TypeScript
- Tailwind CSS
- shadcn/ui if available
- Local JSON or in-memory storage for the first demo version
- Create AWS-ready service files so the app can later connect to:
  - Amazon Cognito for auth
  - Amazon DynamoDB for project data
  - Amazon S3 for uploads
  - Amazon Bedrock for AI feedback
  - Amazon CloudWatch for logs

Important:
Do not require real AWS credentials for the first working version.
Create a mock AI feedback service first.
Also create an optional Amazon Bedrock service file that can be enabled later with environment variables.
Never hardcode secrets.
Include a .env.example file.

Pages to build:
1. Home page
   - Hero title: “BuilderHub AI”
   - Subtitle: “Turn student ideas into production-ready cloud projects.”
   - Buttons: “Submit a Project” and “View Projects”
   - Small section explaining the flow: Idea → AI Feedback → AWS Architecture → Ship

2. Projects page
   - Show project cards
   - Each card should include:
     - Project name
     - Problem statement
     - Target users
     - Status
     - Suggested AWS services
   - Include sample projects relevant to Kenya student builders, for example:
     - Campus event assistant
     - AI agriculture advisory app
     - Student study resource finder
     - Community helpdesk chatbot

3. Submit Project page
   - Form fields:
     - Project name
     - Problem statement
     - Target users
     - Current stage
     - Main challenge
   - On submit, save the project locally and redirect to a project detail page.

4. Project Detail page
   - Show the submitted project.
   - Add a button: “Get AI Feedback”
   - When clicked, call an API route that returns structured AI feedback.
   - Display feedback in clean cards:
     - Improved problem statement
     - Recommended AWS architecture
     - Security checklist
     - Cost optimization tips
     - 7-day action plan

5. Dashboard page
   - Show simple stats:
     - Total projects
     - Projects needing feedback
     - Most common AWS services
     - Recently submitted projects

API routes:
- POST /api/projects
- GET /api/projects
- GET /api/projects/[id]
- POST /api/ai-feedback

Mock AI feedback:
The mock AI should generate useful feedback based on the submitted project text.
Make it feel realistic and specific, not generic.

AWS-ready architecture:
Create a folder called /lib/aws with:
- bedrock.ts
- dynamodb.ts
- s3.ts
- cognito-notes.md

In bedrock.ts:
- Add a placeholder function for calling Amazon Bedrock.
- Use environment variables:
  - AWS_REGION
  - AWS_ACCESS_KEY_ID
  - AWS_SECRET_ACCESS_KEY
  - BEDROCK_MODEL_ID
- Keep the mock implementation as the default unless USE_BEDROCK=true.

UI style:
Use a dark AWS-inspired theme:
- Dark navy background
- Orange, blue, purple, and green accents
- Clean cards
- Rounded corners
- Professional conference-demo look
- Make it match an AWS Student Builder Group presentation style.

Demo flow:
The final app should support this live demo:
1. Open homepage.
2. Show project cards.
3. Submit a new project idea.
4. Open the project detail page.
5. Click “Get AI Feedback”.
6. Explain how this maps to AWS:
   - Frontend: Amplify Hosting
   - API: API Gateway + Lambda
   - Data: DynamoDB + S3
   - AI: Amazon Bedrock
   - Identity: Cognito
   - Observability: CloudWatch
   - Delivery: GitHub Actions + CDK/Terraform

Code quality:
- Use clean component structure.
- Use TypeScript types.
- Add comments where useful.
- Avoid overengineering.
- Make sure the app runs with:
  npm install
  npm run dev

Deliverables:
- Full working Next.js app
- Clean UI
- Mock data
- AI feedback endpoint
- AWS-ready service placeholders
- README.md with:
  - How to run locally
  - Demo script
  - AWS architecture mapping
  - Next steps for deploying to AWS Amplify
