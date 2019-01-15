+++
date = "2019-01-27T00:00:00+08:00"
draft = true
mathjax = true
tags = []
title = "test"

+++
```python
fig, ax = plt.subplots(figsize=(20,9))
npre = 4
ax.set(title='Filling Missing Data', xlabel='Date', ylabel='Electricity Meter Reading')
filled_elec.loc[(filled_elec.index > '2017-11-14') & (filled_elec.index < '2017-12-1') & (filled_elec.index < '2017-12-1') & (filled_elec.index < '2017-12-1')].value.plot(ax=ax, label='Filled', c='blue')
df.loc[(df.index > '2017-11-14') & (df.index < '2017-12-1')].Electricity.plot(ax=ax, label='SVR', c='orange')
elec.loc[(elec.index > '2017-11-14') & (elec.index < '2017-12-1')].value.plot(ax=ax, label='Original', c='red')
#plt.plot(range(len(elec[-744:])), elec[-744:].values, label='Original', color='orange')
plt.legend(fontsize='large', loc='upper right')
```