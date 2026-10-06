# Study Protocol

How each study session works. Progress lives in [progress.md](progress.md).

## The loop for each subtopic

1. **Learn.** Claude names the matching README section and suggests 1-2 videos. The student watches and asks Claude questions until the idea is clear.
2. **Solve.** The student solves the subtopic's 5 problems on LeetCode alone, no code on the laptop. Hints are graded: nudge first, then name the pattern, and only then walk through the solution. Never give a full solution before the student has tried.
3. **Report.** The student says they are done. Claude marks the 5 problems `[x]` and the subtopic `In progress`.
4. **Verbal quiz.** Claude asks:
   - 3-5 concept questions: definition, when to use it, time and space complexity, common mistakes.
   - 2-3 new problems on the same pattern (not the 5 already done). The student answers in plain text, not code: approach, data structures, complexity, edge cases. Claude probes with follow-ups ("what if the input is empty?", "can you do it in O(1) space?").
5. **Log weak spots.** Anything shaky goes in the subtopic's `Weak spots` line in progress.md.
6. **Revise.** Claude re-teaches each weak spot, gives a short targeted drill, and re-asks it. When it holds, tick `Verbal quiz done`, set the subtopic `Completed`, and move `Current subtopic` forward.

## Topic checkpoint

When every subtopic in a topic is `Completed`:

1. Claude picks 5 new problems that span the whole topic (not already in the list; Easy/Medium only; weighted toward logged weak spots) and writes them under `Checkpoint problems`.
2. The student solves them, then does an overall refresher: a video if they want one, plus a spoken quiz that mixes subtopics.
3. Mark the topic checkpoint `Completed`.

## Active recall and spacing

- At the start of each session, Claude asks 2-3 quick recall questions from earlier completed topics, favoring older ones and logged weak spots.
- A weak spot that shows up again stays logged until it is answered correctly in two separate sessions.

## Rules

- Problems are Easy and Medium only for now. The list ramps from mostly Easy to a mix.
- Update progress.md at the end of every session and commit it, so progress survives between sessions.
- Do not edit README.md when tracking progress; all state lives in `study/`.
