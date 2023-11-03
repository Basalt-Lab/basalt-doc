# **Contributing to Basalt Core**

## **Introduction**

Contributions are what make the open-source community an incredible place to learn, inspire, and create.  
Every contribution you make is highly appreciated.

Whether you're helping correct bugs, proposing new features, updating documentation, or improving coding styles, you're helping make our project stronger and more beneficial for the community.

Follow the steps below to make your contribution.

## **Contribution Process**

```mermaid
gitGraph:
options
{
    "nodeSpacing": 150,
    "nodeRadius": 10
}
end
commit
branch new-feature
checkout new-feature
commit
branch feature
checkout feature
commit
commit
checkout new-feature
merge feature
checkout main
merge new-feature
```

1. **Fork** the project  
    Start by creating a fork of the repository on GitHub. This will help you create your own copy of the project on your account, allowing you to make changes to it freely.
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)  
    Create a new branch to work on your feature.
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)  
    Once you've finished your changes, you can commit them and prepare them for push.
4. **Push** to the branch (`git push origin feature/AmazingFeature`)  
    Once you've finished your changes, you can push them to your fork.
5. Open a **Pull Request** to the `stage` branch  
    Once you've pushed your changes to your fork, you can open a Pull Request to the `stage` branch of the main repository.
6. After your Pull Request is validated, your branch will be **merged** into `stage` and deleted.  
    Once your Pull Request has been validated, your branch will be merged into `stage` and deleted.

!!! warning "Note"
    Be sure to always update your local branch with the `stage` branch before starting work on a new feature to ensure you're working with the latest version of the project.

## **Additional Notes**

Ensure you test all your changes and add tests when possible.
Projects with a full test suite rely on contributions to maintain test coverage.

Check the coding style guidelines and specific project contribution guides (if they exist) to ensure your contribution aligns with the project's expectations.

Remember to update the documentation as necessary to reflect your changes, especially if you are adding or modifying features.

Be open to feedback and actively engaged in discussion on your pull request if community members or maintainers have questions or concerns.

## **Conclusion**

Your time and skills can greatly benefit the project and the community as a whole.

We look forward to seeing your contributions and are ready to collaborate to integrate new ideas or improvements.

Thank you for contributing to making **Basalt Core** even better!
