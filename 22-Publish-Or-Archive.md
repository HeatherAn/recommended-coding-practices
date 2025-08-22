# Publish or Archive

In this section you will find guidelines on what to do once you are ready to publish or archive a version of the code project.

## What do we consider by a *project*?

As mentioned in the [Project Structure](https://github.com/HeatherAn/recommended-coding-practices/blob/main/09-Project-Structure.md) section, as a rule-of-thumb a proper (code) *project*, aside a directory containing the code scripts, it should have as a minimum:  

- a **README** file  
- a **LICENSE** file  
- a **notebook**  
- a **data** folder  
- and a static copy of the **raw (original) data** 

During the development of the code, we have recommended to **ignore the data files** when updating the *remote* repository and doing version control on the files of the project. This recommendation comes from the fact that a service like Github is not a *data repository* nor a *data archive*. 

In the following, we will consider the *data* as something separate from *the (code) project*. More strictly speaking, once the work is finished, we will consider *the project* as the **code scripts, README file, LICENSE file and notebook** (remember the notebook should point/refer to an exemplifying dataset, which is a small subset of the data you use in the project). The *data* you used in the research will be considered separately from *the project*.


## What to do once you finish *the project*?

Once *the project* is finalized (or there is a version that can be considered worth-keeping for the long-term), there are mainly two options to follow: **archive** or **publish**.

- In this material we consider **archiving** as securely storing the project in a **private** repository for the long-term. The *code project* is then accessible only to some people (e.g. your supervisor).  
- By **publishing** we consider that the *code project* will be publicly shared (e.g. via a public Github repository), and a static copy of it will be published in a *proper research data platform* such as [4TU.ResearchData](https://data.4tu.nl/), [Zenodo](https://zenodo.org/) or [Dataverse](https://dataverse.org/), among others. In this way, the static copy of the *code project* receives a **persistent identifier** (e.g. a DOI) making it **findable**, **citable** and **accessible** in the long-term.  

Which option to take will depend on different things and of course you should **first discuss it** with your supervisor(s) and collaborators. In general, *in-house developments* are kept privately so that future students and researchers of your institution can reuse the code and build upon it exclusively.

The option of **publishing** is for developments where there are no commercial constraints nor your institution wants to make exclusive use of. Publishing the project (and code) **openly** has several benefits:

- It shows **transparency** (increases **reproducibility** in the field!).
- It allows you to **disseminate** further the work you and your collaborators did.
- *The project* can become **citable**.
- It allows others to **reuse** such knowledge and **build upon it!**

In the following, we will specify what to do for each one of the steps mentioned above for both *the project* and the *data*.

## Option 1: archiving (keeping it private)

In this case, make sure the relevant team members have the proper access rights (e.g., supervisor and collaboratos have either `Maintainer` or `Owner` rights). You can manage access rights to others by going to the Github repository **Settings** > **Collaborators** > **Manage Access**.

Assuming you have been following all recommendations presented in this material, make sure:  

- the **code scripts** are properly structured and documented; 
- the **README** of the repository is complete;
- the **LICENSE** file has been updated accordingly (consider your institution's guideline on intellectual property regarding software);
- the **notebook** is complete and refers to an **exemplifying dataset** that is findable and accessible at least to your supervisor(s) (and collaborators if applicable). In fact, depending on whether the exemplifying dataset can be published *(released publicly)* or not *(needs to remain private)*, the exemplifying dataset can be stored for the long-term in one of the following options:
    - a *public* or *private* repository such as [4TU.ResearchData](https://data.4tu.nl/), [Zenodo](https://zenodo.org/) or [Dataverse](https://dataverse.org/), among others;  
    - a known database in your field (provide the reference to it in the notebook);  
    - at an **restricted-access** drive within your institution's network (accessed by your supervisor(s) and collaborators for the long-term);  
 

# Option 2: publishing (sharing it openly!)

In this case the recommendation is to have the *code project* in a public Github repository. 

Make sure you **add a proper license** to it (in the **LICENSE** file you kept empty during the development). Not sure which license to use? Check out [this link](https://choosealicense.com/) for information on licenses. Recommended **open-source licenses** are the [MIT License](https://choosealicense.com/licenses/mit/) and the [Apache License 2.0](https://choosealicense.com/licenses/apache-2.0/). For more licenses and their description see [this link](https://choosealicense.com/licenses/). If you have any further questions, contact the Data Steward or similar research data/code management support staff available at your institution.

Once the Github public repository is created, **archive a snapshot of the Github repository in a proper research data platform** like the [4TU.ResearchData](https://data.4tu.nl/), [Zenodo](https://zenodo.org/) or [Dataverse](https://dataverse.org/), among others. Why the need of doing this? Github like Gitlab and analogue services do not provide **persistent identifiers** (such as a [DOI](https://www.doi.org/) or [handle](http://www.handle.net/)). Good news is that [4TU.ResearchData](https://data.4tu.nl/) and [Zenodo](https://zenodo.org/) currently provide an integration with Github so that with a single step, a snapshot of the Github repository (at a given point in time) can be properly archived in their platform with a persistent identifier (a DOI) assigned to it. In this way the *code project* becomes *findable*, *accessible* and *citable* in the long-term (10-15 years).

**How can you do this integration?** See [this reference](https://guides.github.com/activities/citable-code/) for **Zenodo**, and [this reference](https://data.4tu.nl/info/about-your-data/getting-started) for **4TU.ResearchData** archive.  

 
Regardless if you use the **4TU.ResearchData** or **Zenodo** integration, make sure you specify the same license as the one you specified in the Github repository.

Regarding the **exemplifying dataset** used in the notebook, make sure it is available to everyone. If the exemplifying dataset is small enough (of the order of MBs) you can add it to the Github repository. If it *has* to be greater than that (remember the exemplifying dataset should be small), then the exemplifying dataset can be published in a **public** [4TU.ResearchData](https://data.4tu.nl/info/en/) or [Zenodo](https://zenodo.org/) **repository**. 

In both the 4TU.ResearchData and Zenodo, uploaded datasets are given a **persistent identifier** (a DOI) which you should refer to in the **README** and/or notebook of the Github repository. Likewise, do not forget to add the persistent identifier of the respective snapshot of the Github repository in the information of the exemplifying dataset repository.

When uploading *data* to the 4TU.ResearchData or Zenodo, you will be asked to provide a license to the uploaded datasets. In this case you should use proper *content* licenses. Examples of **open-content** licenses are the [Creative Commons](https://creativecommons.org/share-your-work/). The recommended **open-content** license that should be considered by default is the [CC-BY](https://creativecommons.org/licenses/by/4.0/). This license essentially says *use it in whichever way, but cite me on it*. 

Assuming you have been following all recommendations presented in this Wiki, make sure:  

- the **code scripts** are properly structured and documented;  
- the **README** of the repository is complete;  
- the **LICENSE** file has been updated accordingly;  
- the **notebook** is complete and refers to an **exemplifying dataset** findable and accessible to everyone as mentioned above. 
 
# What happens to the *data*?

Regarding the rest of the *data* used in the research, if the *data* can be shared with everyone, proceed to store it in a **public** [4TU.ResearchData](https://data.4tu.nl/info/en/) or [Zenodo](https://zenodo.org/) **repository**. Follow the same recommendations as mentioned above.

If the **data** may only be shared with some (either only your supervisor(s) and collaborators), consider storing the data for the long-term in one of the following options:  
- a *private* repository at [Zenodo](https://zenodo.org/) or [Dataverse](https://dataverse.org);  
- at a **restricted-access** drive within your institution's network accessed by your supervisor(s) (and collaborators if applicable).


Do you have any questions or want feedback about how to publish the code and data? Contact the Data Steward or related research data/code management support available at your institution.


________________________

[Previous : 16 - Coding Check Tools](https://github.com/HeatherAn/recommended-coding-practices/blob/main/16-Coding-Check-Tools.md)  
[Next : 18 - Environment Variables](https://github.com/HeatherAn/recommended-coding-practices/blob/main/18-Environment-Variables.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)