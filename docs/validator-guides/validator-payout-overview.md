# **VALIDATOR PAYOUT OVERVIEW**

## **Era Points**

For every era (a period of time), validators are paid proportionally to the amount of era points they have collected. 
Era points are reward points earned for payable actions like:

- producing a block in the Chain.
- producing a reference to a previously unreferenced uncle block.
- producing a referenced uncle block.

!!! NOTE
    An uncle block is a Chain block that is valid in every regard but fails to become canonical/standard. This can happen when two or more validators produce two different blocks nearly simultaneously. Both blocks are valid productions and could act as an accurate reference for the next block producer. However, the chain decides on a strain of blocks that carry the most weight. The block that was valid but was discarded from the canon is called an uncle block. Since uncles are proper productions, the creation of uncles is getting rewarded.

Payments occur at the end of every era.

---

## **Payout Scheme**

No matter how much total stake is behind a validator, all validators split the block-authoring payout equally. However, the payout of a specific validator may differ based on era points, as described above. Although there is a probabilistic component to receiving era points, and they may be impacted slightly depending on factors such as network connectivity, well-behaving validators should generally average out to having similar era point totals over a large number of eras.

Validators may also receive "tips" from senders as an incentive to include transactions in their produced blocks. Validators will receive 100% of these tips directly.

Validators will receive staking rewards in the form of the native coins of that chain (ZEP for Zukma Network).

For simplicity, the examples below will assume all validators have the same amount of era points, and received no tips.

```
Validator Set Size (v): 4

ACTIVE SET
Validator 1 Stake (v1): 18 coins
Validator 2 Stake (v2):  9 coins
Validator 3 Stake (v3):  8 coins
Validator 4 Stake (v4):  7 coins

PAYOUT END OF THE ERA
Payout (p): 8 ZEP

PAYOUT CALCULATION
Payout for each validator (v1 to v4):
Payout = p / v = 8 / 4 = 2 ZEP per validator in the active set
```

Note that this is different than most other Proof-of-Stake systems such as Cosmos. As long as a validator is in the validator set, it will receive the same block reward as every other validator. Validator v1, who had 18 coins staked, received the same reward (2 coins) in this era as v4, with only seven tokens staked.

---

## **Running Multiple Validators**

A single entity can run multiple validators. Running multiple validators may provide a better risk/reward ratio. Assuming you have enough ZEP, or enough stake nominates your validator to ensure that your validators remain in the validator set, running multiple validators will result in a higher return than running a single validator.

For the following example, assume you have 18 ZEP to stake. For simplicity's sake, we will ignore nominators. As in the example above, running a single validator would net you 2 ZEP in this era.

Note that while ZEP is used as an example, this same formula would apply to ZEP when running a validator on Zukma Network

```
Validator Set Size (v): 4

ACTIVE SET
Validator 1 Stake (v1): 18 coins <- YOUR VALIDATOR
Validator 2 Stake (v2):  9 coins
Validator 3 Stake (v3):  8 coins
Validator 4 Stake (v4):  7 coins

PAYOUT END OF THE ERA
Payout (p): 8 ZEP

PAYOUT CALCULATION
Your Payout = p / v = 8 / 4 = 2 ZEP 
```

Running two validators, and splitting the stake equally, would result in the original validator `v4` being kicked out of the validator set, as only the top v validators (as measured by stake) are selected to be in the validator set. More important, it would also double the reward that you get from each era.

```
Validator Set Size (v): 4

ACTIVE SET
Validator 1 Stake (v1): 9 coins <- YOUR FIRST VALIDATOR
Validator 2 Stake (v2): 9 coins <- YOUR SECOND VALIDATOR
Validator 3 Stake (v3): 9 coins
Validator 4 Stake (v4): 8 coins

PAYOUT END OF ERA
Payout (p): 8 ZEP

Your payout = (p / v) * 2 = (8 / 4) * 2 = 4 ZEP
```
With enough stake, you could run more than two validators. However, each validator must have enough stake behind it to be in the validator set.

The system is designed to favor equally-staked validators. This works out to be a dynamic, rather than static, equilibrium. Potential validators will run different numbers of validators and apply different amounts of stake to them as time goes on and in response to the actions of other validators on the network.

---

## **Slashing**
Although the system pays rewards equally, slashes are relative to a validator's stake. Therefore, if you do have enough ZEP to run multiple validators, it is in your best interest to do so. Of course, a slash of 30% will be more ZEP for a validator with 18 ZEP staked than one with 9 ZEP staked.

Running multiple validators does not absolve you of the consequences of misbehavior. The network punishes attacks that appear coordinated more severely than individual attacks. You should not, for example, run multiple validators hosted on the same infrastructure. A proper multi-validator configuration would ensure that they do not fail simultaneously.

Nominators have the incentive to nominate the lowest-staked validator, as this will result in the lowest risk and highest reward. This is because while their vulnerability to slashing remains the same (since it is percentage-based), their rewards are higher since they will be a higher proportion of the total stake allocated to that validator.

To clarify this, let us imagine two validators, JOHN and BOBBY. Assume both are in the active set, have commission set to 0%, and are well-behaved. The only difference is that BOBBY has 90 ZEP nominating it and JOHN only has 10. If you nominate BOBBY, it now has 90 + 10 = 100 ZEP, and you will get 10% of the staking rewards for the next era. 

If you nominate JOHN, it now has 10 + 10 = 20 ZEP nominating it, and you will get 50% of the staking rewards for the next era. In actuality, it would be pretty rare to see such a significant difference between the stake of validators, but the same principle holds even for more minor differences. If there is a 10% slash of either validator, you will lose 1 ZEP in each case.

---

## **Nominators and Validator Payments**
Nominated stake allows you to "vote" for validators and share in the rewards (and slashing) without running a validator node yourself. Validators can choose to keep a percentage of the rewards due to their validator to "reimburse" themselves for the cost of running a validator node. Other than that, all rewards are shared based on the stake behind each validator. This includes the stake of the validator itself, plus any stake bonded by nominators.

!!! Note
    Validators set their preference as a percentage of the block reward, not an absolute number of ZEP. The block rewards are based on the total amount at stake, with the reward peaking when the amount staked is at 50% of the total supply. The commission is set as the amount taken by the validator; that is, 0% commission means that the validator does not receive any proportion of the rewards besides that owed to it from self-stake, and 100% commission means that the validator operator gets all rewards and gives none to its nominators.

The following examples show the results of several different validator payment schemes and the split between nominator and validator stake. We will assume a single nominator for each validator. However, there can be numerous nominators for each validator. Rewards are still distributed proportionally - for example, if the total rewards to be given to nominators is 2 ZEP, and there are four nominators with equal stake bonded, each will receive 0.5 ZEP. Note also that a single nominator may stake different validators.

Each validator in the example has selected a different validator payment (a percentage of the reward set aside directly for the validator). The validator's payment percentage (in ZEP, although the same calculations work) is listed in brackets ([]) next to each validator. Since the validator payment is public knowledge, having a low or non-existent validator payment may attract more stake from nominators, since they know they will receive a larger reward.

```
Validator Set Size (v): 4

ACTIVE SET (One Nominator per Validator)
Validator 1 Stake (v1) [20% commission]: 18 ZEP (9 ZEP self-stake, 9 ZEP nominator-stake)
Validator 2 Stake (v2) [40% commission]:  9 ZEP (3 ZEP self-stake, 6 ZEP nominator-stake)
Validator 3 Stake (v3) [10% commission]:  8 ZEP (4 ZEP self-stake, 4 ZEP nominator-stake)
Validator 4 Stake (v4) [0% commission]:   6 ZEP (1 ZEP self-stake, 5 ZEP nominator-stake)

TOTAL PAYOUT END OF ERA
Payout (p): 8 DOT

PAYOUT PER VALIDATOR
Payout for each validator (v1 - v4):
p / v = 8 / 4 = 2 ZEP

---------------------------------------------------------------------------------------------------

REWARD CALCULATION - VALIDATOR 01
v1:
(0.2 * 2) = 0.4 ZEP             -> validator payment
(2 - 0.4) = 1.6 ZEP             -> shared between all stake
(9 / 18) * 1.6 = 0.8 ZEP        -> validator self-stake share
(9 / 18) * 1.6 = 0.8 ZEP        -> nominator stake share

v1 validator total reward: 0.4 + 0.8 = 1.2 ZEP
v1 nominator reward: 0.8 ZEP

---------------------------------------------------------------------------------------------------

REWARD CALCULATION - VALIDATOR 02
v2:
(0.4 * 2) = 0.8 ZEP              -> validator payment
(2 - 0.8) = 1.2 ZEP              -> shared between all stake
(3 / 9) * 1.2 = 0.4 ZEP          -> validator self-stake share
(6 / 9) * 1.2 = 0.8 ZEP          -> nominator stake share

v2 validator total reward: 0.8 + 0.4 = 1.2 ZEP
v2 nominator reward: 0.8 ZEP

---------------------------------------------------------------------------------------------------

REWARD CALCULATION - VALIDATOR 03
v3:
(0.1 * 2) = 0.2 ZEP              -> validator payment
(2 - 0.2) = 1.8 ZEP              -> shared between all stake
(4 / 8) * 1.8 = 0.9 ZEP          -> validator self-stake share
(4 / 8) * 1.8 = 0.9 ZEP          -> nominator stake share

v3 validator total reward: 0.2 + 0.9 ZEP = 1.1 ZEP
v3 nominator reward: 0.9 ZEP

---------------------------------------------------------------------------------------------------

REWARD CALCULATION - VALIDATOR 03
v4:
(0 * 2) = 0 ZEP                  -> validator payment
(2 - 0) = 2.0 ZEP                -> shared between all stake
(1 / 6) * 2 = 0.33 ZEP           -> validator self-stake share
(5 / 6) * 2 = 1.67 ZEP           -> nominator stake share

v4 validator total reward: 0 + 0.33 ZEP = 0.33 ZEP
v4 nominator reward: 1.67 ZEP
```

<br></br>

<p align=right> Written by Zukma Team </p>
