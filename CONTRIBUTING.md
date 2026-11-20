# Contributing to Clearpath Robotics repositories

Thanks for your interest in improving our open source software! These guidelines apply to every
repository in the [clearpathrobotics](https://github.com/clearpathrobotics) organization that does
not provide its own `CONTRIBUTING.md`. If a repository has its own guide, follow that one instead,
as it covers repository-specific details such as CI jobs and cross-repository workflows.

## Getting started

1. Fork the repository and clone your fork.
2. Create a feature branch off the default branch for the ROS 2 distro you are targeting
   (e.g. `jazzy`):

   ```bash
   git checkout -b my-feature jazzy
   ```

3. Build the workspace and source it:

   ```bash
   rosdep install --from-paths src --ignore-src -r -y
   colcon build --symlink-install
   source install/setup.bash
   ```

4. If the repository has a `.pre-commit-config.yaml`, install the pre-commit hooks (one-time
   setup):

   ```bash
   pip install pre-commit
   pre-commit install
   ```

## Linting

Repositories that use [pre-commit](https://pre-commit.com/) run linting and formatting checks
before each commit. Run them against the whole tree before pushing:

```bash
pre-commit run --all-files
```

## Coding style

- Python: follow [PEP 8](https://peps.python.org/pep-0008/) with a 100-character line limit.
- C++: follow the [ROS 2 code style](https://docs.ros.org/en/rolling/The-ROS2-Project/Contributing/Code-Style-Language-Versions.html).
- Keep changes focused and scoped to the package you are modifying, and avoid unrelated refactors
  in the same pull request.

## Tests

Build and run the tests through `colcon`:

```bash
colcon build --symlink-install
colcon test --packages-select <package_name>
colcon test-result --verbose
```

Please add or update tests for any behavior you change.

## Submitting a pull request

1. Make sure the workspace builds and `colcon test` passes.
2. Push your branch and open a pull request against the branch you started from.
3. Fill out the pull request template with a clear description of what the change does and why.
   Link any related issues and any related pull requests in other repositories.

## Reporting issues

Please open issues on the GitHub issue tracker of the affected repository and fill out the bug
report template, which walks you through the details we need to reproduce the problem.

## License

By contributing, you agree that your contributions will be licensed under the license that covers
the repository you are contributing to.
