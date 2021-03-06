# Engineering methodology

Date: 2018-04-12

* [Intro](#intro)
* [History](#History)
* [Objectives and Key Results (OKRs)](#objectives-and-key-results-okrs)
* [Kanban](#kanban)
  * [Company Kanban](#company-kanban)
  * [Team Kanban](#team-kanban)
    * [How to pick next issues to worked on?](#how-to-pick-next-issues-to-work-on)
* [Leads Meeting](#leads-meeting)
* [Team Meeting](#team-meeting)
* [Standup](#standup)
* [Demo](#demo)
* [Keeping track of things](#keeping-track-of-things)
* [Definitions](#definitions)
  * [What does TODO mean?](#what-does-todo-mean)
  * [What does Done mean?](#what-does-done-mean)
  * [What does Blocker mean?](#what-does-blocker-mean)

## Intro

This document describes the current development methodology followed by engineering.

We use simple, company and team-level Kanban boards,
so that all iterations including planning/work/retrospective do not happen
synchronously at the same weeks for all the teams.

Meetings for high-level sync including product direction, vision, etc are
proactively scheduled by each Team Lead as needed. All Leads have periodical
hands-on meetings with the CTO.

## History

source{d} has gone through two major methodology changes:

* Initially, a partial scrum implementation was used.
* In 2017, we transitioned to a more complete scrum implementation.
* In 2018Q1 we replaced scrum with a simpler Kanban model, which is our current methodology.

## Objectives and Key Results (OKRs)

Management publishes OKRs at the beginning of every quarter. Starting from 2018Q2, OKRs are published in the [src-d/okrs](https://github.com/src-d/okrs) repository.

Each team is expected to publish its own OKRs, aligned with the company ones.
Engineering has team-level objectives, not individual ones. Only tasks in the backlog are expected to have individual assignments.

## Kanban

The Kanban board is a tool used to visualize work and optimize the flow of the work
among the team. ([source](https://www.atlassian.com/agile/kanban#kanban-boards))

The Kanban relies upon full transparency of work and real-time communication of
capacity. Therefore the Kanban board should be seen as the single source of
truth for the team's work.

The Kanban columns are defined as follows:

### [Company Kanban](https://github.com/orgs/src-d/projects/9)

Column      | Description
------------|------------
Backlog     | Only contains Epics and user stories.
TODO        |
In Progress |
Done        |

### Team Kanban

Each team uses separate [Github Projects](https://github.com/orgs/src-d/projects/) as a Kanban board.

Teams managing issues across different Github Orgs (i.e Applications, Language Analysis) are using the “add card” trick, described in [dear-github/dear-github#209](https://github.com/dear-github/dear-github/issues/209#issuecomment-357692288) to add issues from a different org.


Column           | Description
-----------------|------------
Backlog          | Break-down of the Epics for each product on actual tasks
TODO             | Tasks from backlog that are immediately ready to be acted on. Grooming a backlog to update this column is expected to be done on a daily basis by the Lead. See the Definition of TODO section below.
Development      | Assigned task from TODO that time has been spent up on.
Code Review (PR) | Issues that have PRs and are ready for Code Review.
Deploy/Release   | Things that are implemented/merged, but have not yet been “delivered” to the users. This can be seen as a next release “backlog”. Release itself, although is not trivial and is documented <elsewhere>, is not expected to be handed in a separate issue.
Done             | A task is done, when  a user can use the results of the work though established interface: package manager for libs, online for web services, etc. See the section below [What does TODO mean?](#what-does-todo-mean).

On *"blockers"* - a task can be blocked at any stage of the development, so
there is no separate column and Tag is used instead to signify if something is
blocked.

More details in [Definition](#definition) section below.

### How to pick next issues to work on?

Each team decides what works best for them. One effective way is picking tasks
from **right to left** in the Kanban board, choosing from those issues that are
neither assigned to someone nor blocked. A single person should not be in charge
of delivering the whole issue from Development to Done. In that way knowledge is
better spread across the whole team.

For this to work properly, issues must be documented so that a person can move on with the issue, reading what has been done.


## Leads Meeting

Same as something called SoS (Scrum of Scrums) before - a weekly meeting on Tuesdays 14:30 for the CTO
and all team leads to catch up on ongoing progress.

Each team lead will prepare:

* Review on what has been worked last week.
* What are the things we are looking forward to? (re-prioritize things)
* Pitch new ideas from our workflow.

Then grooming company’s backlog/epics from [Company Kanban](https://github.com/orgs/src-d/projects/9) is conducted.

## Team Meeting

A bi-weekly meeting of the CTO with the team lead and optionally with the full
team (to be decided by the lead), in order to comment the status of the
projects. Scheduled with each team individually by CTO.

## Standup

All standups are happening online and asynchronously, per-team in appropriate
`su-*` Slack channels. Standup reports are managed through Slack private messages with [geekbot](https://geekbot.io/).

## Demo

Demo meeting is a monthly event.

* Idea: let everybody know what's going on (on quite technical level) that is relevant for others or affects others’ releases/deployments.
* Product does not need to be deployed, but the demo should be as real as possible.
* Should be concise, respecting other people's time.
* Fixed max time **per-team: 15min (including questions)**. Agree between teams in advance, if more time needed.

## Keeping track of things

Github Projects board will used as a Kanban board.

Teams managing issues across Github Org borders (Applications, Language Analysis) will use the “add card”  trick, described in dear-github/dear-github#209 to  add issues from different org  to the team’s board.

Issues repositories:

* [src-d/issues-general](https://github.com/src-d/issues-general) - should be used more, as place for feedback/requests (i.e website, etc)
* [src-d/issues-infrastructure](https://github.com/src-d/issues-infrastructure) - issues/requests to Infrastructure team must be created here.

# Definitions

Below, we'll define the meaning of each Kanban column.

This is not a mere formality - it’s important to have same things in mind when
moving work from one state to another and what is documented below is a
consensus, that took a few hours to build among Engineering leads.

## What does TODO mean?

Something an engineer can immediately take and act up on. If the task is not
possible to start until another (well-known) task is finished first, this task
shall not be in TODO yet.

*Rationale* there are 2 goals we want to keep in mind, while working with Kanban
board:

* as small TODO list on a Kanban as possible and
* tasks, moving fast from end-to-end of Kanban board (short Cycle Time)

This definition and goals also imply that leads should grooming backlog on a
daily basis.

> Alternative definition (discussed but discarded): all things that are planned to be done ASAP. This would imply that issues can be added to TODO in bulk at once, even in cases when multiple issues of single project have known dependency on one another. Was discarded on the premise that it would go against the 2 goals, listed above.

## What does Done mean?

General mindset: Done always means that a user, both inside and outside src-d,
is able to use it through well-established interfaces. Detailed definition may
vary per-team.

Few concrete examples, in case of work done on:

* Golang library - it should be possible to use them though the particular version published on gopkg.in
* Scala library - it should be possible to use from Maven/sbt build
* Web site/application - should be accessible through a known (staging/production) environment URL
* etc


## What does Blocker mean?

*General mindset*: blocker means something **unexpected has happened**

Obvious/expected dependencies between sequence of tasks don’t need to be marked
as blocked.

Issues from backlog that can not be done, due to **a known dependency** should
**never** go into the TODO column (thus avoid being blocked). I am not able to
work on it anymore, because it needs something done to move forward.

Things that are not *blockers*:

* change of priority (stop working on something for now)
* a known, planned and expected issue (i.e dependency on another team’s work, that is handled in another issue
