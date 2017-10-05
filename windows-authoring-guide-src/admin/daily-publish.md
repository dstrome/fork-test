---
ms-author: v-mikmat
author: mikematteson
---

# Daily OP publishing procedures

<!--
<hr />
<span style="font-family: stencil,arial,verdana;font-size:18pt;color:darkred;opacity:0.4">DRAFT</span>&nbsp;&mdash;&nbsp;<span style="font-weight:bold; color:darkred">This content is not yet ready for use.</span>
<hr />
-->

*Last updated: September 1, 2017*

- **Platform:** docs.microsoft.com
- **Repos:** [windows-uwp](#windows-uwp), [winrt-api](#winrt-api), [winrt-related](#winrt-related), [project-rome](#project-rome) (Not included: cortana, edge-developer, windows-compatibility)
- **Team:** WDG CX Developer

> [!IMPORTANT]
> These instructions are exclusively for those responsible for daily OP publishing&mdash;that is, merging content from the master branch to the live environment and other main branches, and synchronizing content between private and public repositories. Typically these duties belong to a member of the vendor managed service or a member of the WDG OP Scrum (*wdgopscrum*) v-team. **If these functions aren't part of your regular duties, don't perform the procedures described here.** 


## windows-uwp

Branches: <strong>master</strong>, <strong>live</strong>, <strong>rs3</strong>, <strong>neon-design-system</strong>

### First-time local setup or reclone (windows-uwp)

Perform these steps only if you're setting up a fresh local clone.

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git clone https://cpubwin.visualstudio.com/_git/windows-uwp</td><td>Clone local VSTS windows-uwp.</td></tr>
<tr><td>2</td><td style="font-weight:bold">cd windows-uwp</td><td>Change directory to the just-created windows-uwp directory.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git remote add github https://github.com/MicrosoftDocs/windows-uwp.git</td><td>Add remote representing GitHub windows-uwp as “github”.</td></tr>
<tr><td>4</td><td style="font-weight:bold">git remote rename origin vsts</td><td>Rename VSTS “origin” remote as “vsts”.</td></tr>
</table>

### Daily publishing (windows-uwp)

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>2</td><td style="font-weight:bold">git pull vsts master</td><td>Pull latest changes from VSTS remote master branch<br />into local master branch.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git checkout live</td><td>Get on VSTS live branch</td></tr>
<tr><td>4</td><td style="font-weight:bold">git pull vsts live</td><td>Pull latest changes from VSTS remote live branch<br />into local live branch.</td></tr>
<tr><td>5</td><td style="font-weight:bold">git merge master</td><td>Merge VSTS master branch<br />into local live branch.</td></tr>
<tr><td>6</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>7</td><td style="font-weight:bold">git push vsts live</td><td>Push from VSTS local live branch<br />to VSTS remote live branch.</td></tr>
<tr><td>8</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>9</td><td style="font-weight:bold">git pull github docs</td><td>Pull (=merge) latest changes from GitHub remote docs<br />into VSTS local master.</td></tr>
<tr><td>10</td><td style="font-weight:bold">git pull vsts master</td><td>Pull (=merge) latest changes from VSTS remote master<br />into VSTS local master.</td></tr>
<tr><td>11</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td></td></tr>
<tr><td>12</td><td style="font-weight:bold">git push vsts master</td><td>Push from VSTS local master<br />to VSTS remote master.</td></tr>
<tr><td>13</td><td style="font-weight:bold">git push github master:docs</td><td>Push from VSTS local master<br />to GitHub remote docs.<br />**Ensure no spaces on either<br />side of colon (":").**</td></tr>
<tr><td>14</td><td style="font-weight:bold">git checkout rs3</td><td>Get on VSTS rs3 branch</td></tr>
<tr><td>15</td><td style="font-weight:bold">git pull vsts rs3</td><td>Pull latest changes from VSTS remote rs3 branch<br />into local rs3 branch.</td></tr>
<tr><td>16</td><td style="font-weight:bold">git merge master</td><td>Merge VSTS local master branch<br />into local rs3 branch.</td></tr>
<tr><td>17</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>18</td><td style="font-weight:bold">git push vsts rs3</td><td>Push from VSTS local rs3<br />to VSTS remote rs3.</td></tr>
<tr><td>19</td><td style="font-weight:bold">git checkout neon-design-system</td><td>Get on VSTS neon-design-system branch</td></tr>
<tr><td>20</td><td style="font-weight:bold">git pull vsts neon-design-system</td><td>Pull latest changes from VSTS remote neon-design-system branch<br />into local neon-design-system branch.</td></tr>
<tr><td>21</td><td style="font-weight:bold">git merge rs3</td><td>Merge VSTS local rs3 branch<br />into local neon-design-system branch.</td></tr>
<tr><td>22</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>23</td><td style="font-weight:bold">git push vsts neon-design-system</td><td>Push from VSTS local neon-design-system<br />to VSTS remote neon-design-system.</td></tr>
</table>


## winrt-api

Branches: <strong>master</strong>, <strong>live</strong>, <strong>rs3</strong>

### First-time local setup or reclone (winrt-api)

Perform these steps only if you're setting up a fresh local clone.

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git clone https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api</td><td>Clone local VSTS winrt-api.</td></tr>
<tr><td>2</td><td style="font-weight:bold">cd winrt-api</td><td>Change directory to the just-created winrt-api directory.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git remote add github https://github.com/MicrosoftDocs/winrt-api.git</td><td>Add remote representing GitHub winrt-api as “github”.</td></tr>
<tr><td>4</td><td style="font-weight:bold">git remote rename origin vsts</td><td>Rename VSTS “origin” remote as “vsts”.</td></tr>
</table>

### Daily publishing (winrt-api)

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>2</td><td style="font-weight:bold">git pull vsts master</td><td>Pull latest changes from VSTS remote master branch<br />into local master branch.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git pull github docs</td><td>Pull (=merge) latest changes from GitHub remote docs<br />into VSTS local master.</td></tr>
<tr><td>4</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>5</td><td style="font-weight:bold">git push vsts master</td><td>Push from VSTS local master<br />to VSTS remote master.</td></tr>
<tr><td>6</td><td style="font-weight:bold">git checkout live</td><td>Get on VSTS live branch</td></tr>
<tr><td>7</td><td style="font-weight:bold">git pull vsts live</td><td>Pull latest changes from VSTS remote live branch<br />into local live branch.</td></tr>
<tr><td>8</td><td style="font-weight:bold">git merge master</td><td>Merge VSTS master branch<br />into local live branch.</td></tr>
<tr><td>9</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>10</td><td style="font-weight:bold">git push vsts live</td><td>Push from VSTS local live branch<br />to VSTS remote live branch.</td></tr>
<tr><td>11</td><td style="font-weight:bold">git checkout rs3</td><td>Get on VSTS rs3 branch</td></tr>
<tr><td>12</td><td style="font-weight:bold">git pull vsts rs3</td><td>Pull latest changes from VSTS remote rs3 branch<br />into local rs3 branch.</td></tr>
<tr><td>13</td><td style="font-weight:bold">git merge master</td><td>Merge VSTS local master branch<br />into local rs3 branch.</td></tr>
<tr><td>14</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>15</td><td style="font-weight:bold">git push vsts rs3</td><td>Push from VSTS local rs3<br />to VSTS remote rs3.</td></tr>
<tr><td>16</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>17</td><td style="font-weight:bold">git push github master:docs</td><td>Push from VSTS local master<br />to GitHub remote docs.<br />**Ensure no spaces on either<br />side of colon (":").**</td></tr>
</table>

## winrt-related

Branches: <strong>master</strong>, <strong>live</strong>

### First-time local setup or reclone (winrt-related)

Perform these steps only if you're setting up a fresh local clone.

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git clone https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-related</td><td>Clone local VSTS winrt-related.</td></tr>
<tr><td>2</td><td style="font-weight:bold">cd winrt-related</td><td>Change directory to the just-created winrt-related directory.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git remote add github https://github.com/MicrosoftDocs/winrt-related.git</td><td>Add remote representing GitHub winrt-related as “github”.</td></tr>
<tr><td>4</td><td style="font-weight:bold">git remote rename origin vsts</td><td>Rename VSTS “origin” remote as “vsts”.</td></tr>
</table>

### Daily publishing (winrt-related)

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>2</td><td style="font-weight:bold">git pull vsts master</td><td>Pull latest changes from VSTS remote master branch<br />into local master branch.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git checkout live</td><td>Get on VSTS live branch</td></tr>
<tr><td>4</td><td style="font-weight:bold">git pull vsts live</td><td>Pull latest changes from VSTS remote live branch<br />into local live branch.</td></tr>
<tr><td>5</td><td style="font-weight:bold">git merge master</td><td>Merge VSTS master branch<br />into local live branch.</td></tr>
<tr><td>6</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td> </td></tr>
<tr><td>7</td><td style="font-weight:bold">git push vsts live</td><td>Push from VSTS local live branch<br />to VSTS remote live branch.</td></tr>
<tr><td>8</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>9</td><td style="font-weight:bold">git pull github docs</td><td>Pull (=merge) latest changes from GitHub remote docs<br />into VSTS local master.</td></tr>
<tr><td>10</td><td style="font-weight:bold">git pull vsts master</td><td>Pull (=merge) latest changes from VSTS remote master<br />into VSTS local master.</td></tr>
<tr><td>11</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td></td></tr>
<tr><td>12</td><td style="font-weight:bold">git push vsts master</td><td>Push from VSTS local master<br />to VSTS remote master.</td></tr>
<tr><td>13</td><td style="font-weight:bold">git push github master:docs</td><td>Push from VSTS local master<br />to GitHub remote docs.<br />**Ensure no spaces on either<br />side of colon (":").**</td></tr>
</table>

## project-rome 

Branches: <strong>master</strong> <br />
Notes: Sync between VSTS/master and GitHub/master; no updates among branches in the same repo.

### First-time local setup or reclone (project-rome)

Perform these steps only if you're setting up a fresh local clone.

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git clone https://cpubwin.visualstudio.com/project-rome/_git/project-rome</td><td>Clone local VSTS winrt-related.</td></tr>
<tr><td>2</td><td style="font-weight:bold">cd project-rome</td><td>Change directory to the just-created project-rome directory.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git remote add github https://github.com/Microsoft/project-rome.git</td><td>Add remote representing GitHub project-rome as “github”.</td></tr>
<tr><td>4</td><td style="font-weight:bold">git remote rename origin vsts</td><td>Rename VSTS “origin” remote as “vsts”.</td></tr>
</table>

### Daily publishing (project-rome)

<table>
<tr><th>Step</th><th style="text-align:left">Command line</th><th style="text-align:left">Description</th></tr>
<tr><td>1</td><td style="font-weight:bold">git checkout master</td><td>Get on VSTS master branch.</td></tr>
<tr><td>2</td><td style="font-weight:bold">git pull vsts master</td><td>Pull latest changes from VSTS remote master branch<br />into local master branch.</td></tr>
<tr><td>3</td><td style="font-weight:bold">git pull github master</td><td>Pull (=merge) latest changes from GitHub remote master<br />into VSTS local master.</td></tr>
<tr><td>4</td><td style="font-style:italic;color:darkred" colspan="2"><em>Resolve merge conflicts, if any.</em></td><td></td></tr>
<tr><td>5</td><td style="font-weight:bold">git push vsts master</td><td>Push from VSTS local master<br />to VSTS remote master.</td></tr>
<tr><td>6</td><td style="font-weight:bold">git push github master:master</td><td>Push from VSTS local master<br />to GitHub remote master.<br />**Ensure no spaces on either<br />side of colon (":").**</td></tr>
</table>