import numpy as np 
import matplotlib.pyplot as plt
# population
N = 1e7 + 10 + 5
# simuation Time / Day
T = 100
#quarantine number
Q= np.zeros([T])
# susceptiable number
s = np.zeros([T])
#exposed number
e=np.zeros([T])
# infective ratio
i = np.zeros([T])
# remove number
r = np.zeros([T])
#exposed ratio
#k=np.zeros([T])
beta=0.3
# incubation rate
theta=1/7
# recover rate
gamma = 0.154

# initial infective people
e[0]=50
i[0] = 10
s[0] = 1e7 
for t in range(T-1):
    if t<=10:
        p=10
    elif t<=40:
        p=1
    if t<=30:
        q=0
    if t<=90:
        q=0.9
    elif t<=100:
        q=0.6
    else :
        q=1
    e[t + 1] = e[t] + (0.7 * s[t]*p * i[t]/N) + 0.05 * s[t]*p*  e[t]/N - theta * e[t]-gamma*e[t] 
    i[t + 1] = i[t]*(1-q) + theta * e[t] - gamma*i[t]
    Q[t + 1] = Q[t] + i[t]*q - gamma*Q[t]
    s[t + 1] = s[t] - 0.7 * s[t]*p * i[t]/N - 0.05 * s[t]*p * e[t]/N
    r[t + 1] = r[t] + gamma*i[t] + gamma*e[t] +gamma*Q[t]
print(Q[T-1]+r[T-1]+e[T-1]+i[T-1])
fig, ax = plt.subplots(figsize=(10,6))
#ax.plot(s, c='b', lw=2, label='S')
ax.plot(Q, c='r', lw=2, label='Q')
ax.plot(r, c='g', lw=2, label='R')
ax.plot(e, c='y', lw=2, label='E')
ax.set_xlabel('Day',fontsize=20)
ax.set_ylabel('Infective Number', fontsize=20)
ax.grid(1)
plt.xticks(fontsize=20)
plt.yticks(fontsize=20)
plt.legend()
plt.show()
