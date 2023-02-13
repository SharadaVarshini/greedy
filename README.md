# greedy
#this program has been developed using python , where it computes the remaining tasks and the earnings of the employees by taking the input as the start time, end time and earnings.
#code
def maximizeEarnings(n, jobs):
    jobs = sorted(jobs, key=lambda x: x[1])
    total_earnings = 0
    last_end_time = 0
    count = 0
    for job in jobs:
        if job[0] >= last_end_time:
            last_end_time = job[1]
            total_earnings += job[2]
            count += 1
    return [n - count, n * 100 - total_earnings]

n = int(input("Enter the number of Jobs: "))
jobs = []
for i in range(n):
    start, end, earnings = map(int, input("Enter job start time, end time, and earnings: ").split())
    jobs.append([start, end, earnings])
result = maximizeEarnings(n, jobs)
print("The number of tasks and earnings available for others")
print("Tasks:", result[0])
print("Earnings:", result[1])
