# Code Complexity versus Code Change Frequency

Research for if there is correlation between complexity of code and how frequently code gets changed.

We want to discover as we compare different code bases of varying complexity, does the number of pull request merges (changes) correlate to the complexity.

My hypothesis is that as complexity increases, the number of changes decreases.

Factors to consider:
* The number of unique developers making changes. (Do we want to distinguish between authors of PRs versus committers in PR/main branch)
* How far back should we look when analyzing the frequency?
    * 3 months
    * 6 months
    * 1 year
    * 2 years
    * 5 years

## Implementation

* Gather a list of open source projects that are product-focused, like open-core SaaS: https://github.com/vihar/awesome-oss-saas
* For each project,
    * We want to download the code
        * `git clone`
        * (Leaning this way) Download `.zip` files from GitHub
        * Need to determine which way would be better
    * We want to analyze the complexity using a tool like https://github.com/thoughtbot/complexity
    * We want to analyze how many changes were made over a given time period
        * We could analyze the `git log`, but there are concerns about how each project could handle merging (merge vs squash vs rebase)
        * (Leaning this way) We could use GitHub's PR API to gather the list of `Merged` PRs
    * Perform the correlation analysis
        * We need to look into the best way to perform this study

## References

Kudrjavets, G., Nagappan, N., & Rastogi, A. (2023). Are We Speeding Up or Slowing Down? On Temporal Aspects of Code Velocity. arXiv preprint arXiv:2303.04293.
https://arxiv.org/pdf/2303.04293.pdf
