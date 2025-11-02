![[Software_Dev__Plans_to_Solutions.mp4]]
    

# Modern Software Development Methodologies

> [!summary] Exam Analogy: Planning a Road Trip
> 
> - **[[Traditional Life Cycle (TLC)]]:** Plotting _every single turn_ before starting. Very rigid. Changes are difficult.
>     
> - **[[Spiral Model]] & [[Incremental Development]]:** Planning the trip in small stages. Drive a bit, check the weather/budget (**Risk Analysis** / **User Evaluation**), then plan the next bit. Flexible and adapts to change.
>     
> - **[[USDP (Unified Software Development Process)]]:** An incremental approach with clear phases for _planning_ (**Inception/Elaboration**) and _driving_ (**Construction/Transition**). Ensures the right focus (e.g., mapping vs. driving) at the right time.
>     

## 1. Spiral Model & Incremental Development

> [!note] **What is it?** A software development model that combines the iterative nature of prototyping with the controlled, systematic aspects of the waterfall model.
> 
> **Why use it?** To address the major weakness of the [[Traditional Life Cycle (TLC)]]: its failure to handle change and risk. This model is built for flexibility.

- **Core Idea:** Show **progress** through a series of successive, iterative steps (increments). Each "loop" of the spiral is a mini-project.
    

### Key Activities (The Spiral's Quadrants)

1. **Initial requirements gathering & planning:** Determine objectives, alternatives, and constraints for this cycle.
    
2. **Risk Analysis:** _This is the key feature._ Identify and analyze risks (e.g., technical, management, budget). Develop prototypes to understand risks better.
    
3. **Software Development:** Engineer the product for this iteration (develop and test).
    
4. **User Evaluation & Planning:** Client evaluates the increment. Based on feedback, plan the next "loop" of the spiral (or decide to stop). This includes a **"go, no-go" decision**.
    

### Key Concepts (from `chapter_3.pdf`)

- **Iterative Life Cycle:** Functionality is added in each new cycle.
    
- **Philosophy (Gilb, 1988):** Large successful systems often grow from small successful systems.
    
- **Feedback Loop:** Each delivered increment provides **feedback** to the developers, which guides the _next_ increment.
    
- **Release Types:** An iteration can be an **external release** (to the client) or an **internal release** (to the development team only).
    

> [!quote] Gilb's (1988) Critique of Spiral Model
> 
> Gilb argued the Spiral Model might not fully support his view, as it may not emphasize:
> 
> - Producing **high-value/low-cost increments**.
>     
> - Delivering usable increments (e.g., 1-5% of total budget).
>     
> - A **strict time limit** for each cycle (e.g., one month).
>     
> - A defined measure of **productivity** (e.g., quality improvements).
>     

> [!tip] Exam Tip: Spiral vs. TLC
> 
> The biggest difference is Risk Management.
> 
> - **TLC (Waterfall):** Tries to define _all_ requirements at the start. Very poor at handling change.
>     
> - **Spiral Model:** Built to handle change. **Risk analysis** is performed in _every single loop_, allowing the project to adapt.
>     

## 2. Unified Software Development Process (USDP)

> [!note] **What is it?** A well-defined, iterative and incremental framework for software development.
> 
> **Why use it?** It provides a disciplined, structured process that captures industry best practices for modern, complex projects. Think of it as a "grown-up" version of incremental development.

- **Developers:** Jacobson, Rumbaugh, and Booch (1999) (The "Three Amigos").
    
- **Core Feature:** Deeply integrated with [[UML (Unified Modeling Language)]] for modeling the system.
    
- **Structure:** A project consists of **phases** -> which contain **iterations** -> which involve **workflows**.
    

### The Four Phases of USDP (Sequential)

These are project management phases focused on business goals.

1. **Inception:** **Is this project feasible?** Determine the **scope, purpose,** and business case.
    
2. **Elaboration:** **Do we have a stable plan?** **Capture requirements** and define the core system **structure/architecture**. Most high-risk items are addressed here.
    
3. **Construction:** **Build the system.** The main "build" phase, creating the software in a series of iterations.
    
4. **Transition:** **Roll out the system.** **Install the product** and deliver it to end-users (beta tests, training, etc.).
    

### The Five Core Workflows (Technical Activities)

These are the "things you do" in _each_ iteration.

- `[[Requirements]]` (Capturing what the system should do)
    
- `[[Analysis]]` (Understanding and refining the requirements)
    
- `[[Design]]` (How the system will be built)
    
- `[[Implementation]]` (Writing the code)
    
- `[[Test]]` (Verifying the system works)
    

Key Takeaway: Effort Distribution

The effort in each workflow changes depending on the phase:

- **Inception & Elaboration:** Heavy focus on **Requirements** and **Analysis**.
    
- **Construction & Transition:** Heavy focus on **Implementation** and **Testing**.
    

The system is built iteratively. A new increment might be a **reworked version** of a previous one, not just a simple addition.

## 3. User Involvement

> [!note] **What is it?** Involving end-users directly in the development process.
> 
> **Why is it crucial?** To **maximize the chance of success** and ensure the final system is **fit for its intended purpose** (i.e., it actually solves the user's problem). Incremental models _rely_ on this.

### Methods of User Involvement

1. **As Part of the Development Team (Highest Involvement)**
    
    - _Example:_ [[DSDM (Dynamic Systems Development Method)]].
        
    - _How:_ The user is a full-time or dedicated member of the dev team.
        
    - _Benefit:_ Difficulties are identified _immediately_. Users can suggest alternatives on the spot. Leads to a system that strongly meets user needs.
        
2. **Via a Consultative Approach (Medium Involvement)**
    
    - _How:_ Users are invited to regular team meetings, review designs, and provide feedback on prototypes.
        
    - _Benefit:_ Encourages collaboration and ensures users see their feedback being addressed, building trust.
        
3. **In Fact Gathering (Lowest Involvement)**
    
    - _When:_ Typically in the early stages (Requirements Analysis).
        
    - _How:_ Users are interviewed or asked to review documents.
        
    - _Requires:_ Users must have clear expectations about _when_ documents will be ready for review and have enough time allotted.
        

> [!warning] Challenge of User Involvement
> 
> Effective user involvement requires a significant time commitment from users. This can be costly for the client and difficult to schedule ("users have their own jobs to do").

## 4. Computer Aided Software Engineering (CASE)

> [!note] **What are they?** [[CASE Tools]] are software applications that support and automate tasks throughout the _entire_ software development lifecycle.
> 
> **Why use them?** To manage complexity, improve quality, and increase productivity in large-scale projects.

- **Scope:** Provide support for nearly _all_ development tasks, often as an integrated suite of products (an "I-CASE" or Integrated CASE).
    

### Key Features (from `05_Avoiding_the_Problems.pdf`)

- **Syntactic Correctness Checks:** Ensures diagrams and models follow the rules (e.g., "is this UML diagram valid?").
    
- **Repository Support:** A central "encyclopedia" or "data dictionary" for _all_ system elements (data definitions, models, requirements).
    
- **Consistency & Completeness Checks:** Compares different diagrams to ensure they align (e.g., "does the data in this diagram match the data in that one?") and finds missing info.
    
- **Navigation to Linked Diagrams:** Essential for complex systems, allowing **easy movement** between related parts.
    
- **Layering:** Manages complexity by allowing developers to view the system at different levels of abstraction (high-level overview vs. detailed components).
    
- **Requirements Tracing:** Makes it possible to track _every element_ (like a piece of code) back to a _specific user requirement_.
    
- **Report Generation:** Automatically generates documentation.
    
- **Code Generation:** Automatically generates program code (e.g., database schemas, application skeletons) from design models.
    
- `System simulation & Performance analysis`
    

> [!tip] Exam Tip: Benefits of CASE Tools
> 
> CASE tools are critical for ensuring quality and consistency. They:
> 
> - Aid and **automate documentation**.
>     
> - **Reduce time and effort** for analysts and designers.
>     
> - Automate tasks (like code/report generation), which **reduces the chance of human error**.
>     
> - Enforce standards and consistency via the central **repository**.
>