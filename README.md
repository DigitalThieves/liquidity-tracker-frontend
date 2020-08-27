# Liquidity Tracker

## Goal
We were charged by J. Lassing at Qamcom to develop this over 1,5 yrs ago and lets just say we did and it failed. It wasn't good, barely functioning and we didnt have the tech savyness back then to make it awesome but that could have been managedl. The biog problem is we barely understood the use case and Lassing is a busy man. So the project was a big failure.

However, 18months later, we have a liquidity tracker of our own in Google Sheets and because of that a completely different understanding of the use case, at the very least for our own case.

But there's a reason Lassing didn't want to use Excel for ever and for similar reasons we're also not interested in using our google sheet tracker for all eternity.

As such; we're committed to restart this project and make it awesome!

The short term goal, the MVP so to say, is to have it replace our own google sheets liquidity tracker. Our tracker is pretty basic and straight forward and I understand it completely, both its strength and weaknesses. So making this better than our G.Sheet Tracker ought to be pretty straight forward.

## TODOs

1. Make a frontend MVP with mock data, that functions perfectly as a replacement of our google sheets liq-tracker
- adding and editing entries
- adding and editing companies / cost accounts
- ability to pick VAT percentages
- Format numbers and dates
- Aggregate numbers
- Year view (like the G.sheet tracker, each month being a table of y = customers, x = week in month and x+y => transaction total (SEK) + status (bg color))
- Month view (like the old tracker, a table of y = customer, x = date, comment, status & transaction total amount)
2. Develop a backend to power the frontend. One workspace, one login, shared workspace.
3. Use it for 1-2 months and polish it
4. Make a backend with users and workspaces and shared workspaces
5. Think about auxiliary functions and sign on more members

