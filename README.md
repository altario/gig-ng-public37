# Altar.io Angular FrontEnd Exercise 0220 (Do not fork)

The candidate should write the solution using Angular framework (with Renderer (8) or Ivy(9)) and it's free to use any patterns, methodologies and styling language.
Backend / Operations are not required on this exercise (either way you are free to provide).
Styling is also optional (adhoc scss or CSS utility frameworks preferred over full fledged frameworks ex. Bootstrap, Material)
The exercise involves creating **2 routes**:

- /login/
- /today/

## Steps

1. **Clone** the project to your GitHub account **[DO NOT FORK]**
2. Create a branch with your name (ex: andre-pinto)
3. Develop under that branch
4. Submit a **Pull Request** on your **Repo**
5. Send us an email with your **Repo**

## Pages

You will create the 2 following pages

### Login Page

It's a simple page where the user should be presented with a form in case there is no session / token.
You can emulate the session/cookie by setting a sessionStorage property.
The form contains:

- email (needs to be valid)
- postcode (needs to be valid)
- password
  Validation should run be performed as you the user types

## Today Page

This is a complex page where you will have a long list containing a list of volunteers and the tasks they have been assigned to.
![generator page](https://altario-public.s3-eu-west-1.amazonaws.com/gig37.png)

### Functional Requirements

1. Any of the tasks which the volunteers can work on can be dragged to another volunteer. Example: I can drag the `VIP Support Task` from John to another volunteer which supports it's `type` and `area`.
2. There is a standby pool of tasks the top right corner, where you may want to drag a task into a any volunteer that supports that task `type` and `area`.
3. Between each of the user tasks time you need to fill the gaps with the `waiting time` between the tasks. (computed from `starsAt - endsAt` or `startedAt - endedAt` if already started)
4. The today page will consume 2 JSON files (or API): `unassinged_tasks.json` (for the standby area) which will contain all unassigned tasks and `volunteers.json` which contains all volunteers which the tasks already assigned (for the main list)
5. Implement a local state stategy (you will be updating date locally only, as no API is required on this exercise)

### Non Functional Requirements

1. Every 15 seconds the grid is refreshed with updated data (via a standard HTTP Request, you can mock the different results randomly in case no API is defined)
2. Each of the List rows corresponds to one of the volunteers
3. The list of volunteers provided contains 400 volunteers but can me more
4. Volunteers can have at maximum 6 tasks per day (doesn't matter the time)
5. A Task has a Planned Time, Real Start Time and Real End Time
6. The grid shows the users sorted by group then by name
7. There are 10 timeslot columns representing a normal day from 08h to 18h
8. There is an Area Colummn representing the volunteers operating area
9. Each of the tasks is specific to an area
10. The planned `startsAt` time and `endsAt` time will be different than the real `startedArt` and `endedAt`
11. Each of the volunteers is assigned to multiple areas. See `volunteer.areas[]`
12. Each of the volunteers is assigned to multiple groups. See `volunteer.groups[]`
13. You don't need to update the JSON (PUT or POSTS), but you will need to keep the state on the frontend, i.e., dragging and dropping tasks between users and the standby pool will cause the local state to be updated.
14. Creating an API is optional (as it's technology also)
15. For this exercise purposes assume that all unassigned tasks and volunteer's tasks are only for the current day

### Task Type Enumeration

```ts
enum TaskType {
  'VIP_SUPPORT',
  'CHECK_IN',
  'CHECK_OUT',
  'TENTS',
  'NURSING',
  'MEDICAL',
  'TECH_ADVISE',
  'TECH_SUPPORT'
}
```

### JSON Task Shape

```json
{
  "id": "ws2020324",
  "name": "VIP Support Sector A",
  "type": "VIP_SUPPORT",
  "area": "A16",
  "startsAt": "08:00",
  "endsAt": "12:00",
  "startedAt": "",
  "endedAt": ""
}
```

### JSON Volunteer Shape

```json
{
  "id": "vol23458",
  "name": "John",
  "email": "john@gmail.com",
  "areas": ["A16", "A1"],
  "groups": ["G12", "G1"],
  "tasks": [
    {
      "id": "ws2020324",
      "name": "VIP Support Sector A",
      "type": "VIP_SUPPORT",
      "area": "A16",
      "startsAt": "08:00",
      "endsAt": "12:00",
      "startedAt": "",
      "endedAt": "",
      "volunteer": "vol23458"
    }
  ]
}
```

## Deliverables

- The Angular Application rendering both the login page and today page
- Performance Optimizations UnderTaken
- Profilling and Peformance Tests Undertaken
- NG Architectural Decision Notes
- Unit and Integration Tests (is a plus if at least 25% coverage)

## Questions POC

claudio.teixeira@altar.io
