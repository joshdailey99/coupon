
## Project Background

This project is a practice application that is part of the UC Berkeley ML/AI Professional Certification coursework.

The assignment prompt given was as follows:

#### Analysis Goal

* Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. Would you accept that coupon and take a short detour to the restaraunt? Would you accept the coupon but use it on a subsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaraunt? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?
* Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?
* The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

#### Source Data Used

* This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’. There are five different types of coupons -- less expensive restaurants (under $20), coffee houses, carry out & take away, bar, and more expensive restaurants ($20 - $50).

## Initial Analysis

The assignment offered a starter Jupyter Notebook that prompted the initial loading and review of the source data along with some assigned practice data analysis tasks.

### Initial Findings 

* The overall acceptance rate for all coupons was 56.8%
  
<img src="/images/pie_allcoupons.png">

* When breaking out by coupon type, we see signficant variation in acceptance rates.
  

<img src="/images/bar_allcoupons.png" height="1600px">


## Independent Analysis (Coffee House Coupoons)

The core of ths assignment was to perform an independent data analysis in order to generate actionable insights and offered hypothetical recommendations to business leaders.

For my case, I elected to focus on the data associated with coupons for Coffee Houses alone.  See details below.

### Coffee House Analysis Description

For Coffee House coupons, determine which user and trip attributes are associated with accepting vs rejecting the offer.  Translate those differences into actionable targeting and offer-design suggestions.

### Key Findings 

Top Drivers of Coffee House coupon acceptance:

##### 1 - Time of Day

* 10AM has acceptance rate of 63.9%
* 6PM has acceptance rate of only 41.3%
* Difference of 22.6%

Interestingly, 10AM is higher than the start of day commute time of 7AM. Possibly drivers are too rushed to get to school/work to take advantage of coupons during rush hour. However, 10AM may represent a natural mid-morning break or "second coffee" ritual.  

##### 2 - Prior CoffeeHouse frequency

* Drivers with monthly visits from 4-8 had 68.6% acceptance
* Drivers who never visit had only 18.9%
* Difference of 49.7%

Naturally, drivers who are already established clients of CoffeeHouses will be more attracted to a coupon as opposed to drivers who never visit and may only respond for novelty or price motivations.

##### 3 - Expiration

* If the coupon has 1day until expiration, the acceptance rate is 58.4%
* However, if only 2hours until expiry is offered, the acceptance is only 43.2
* Difference of 15.2%

The longer the offer is valid, the more likely the drivers are to take advantage.  A 2 hour time limit may be too short to allow for personal time conflicts that may not allow the driver to take immediate action on the coupon. 

##### 4 - Destination

* When the destination is No Urgent Place, the acceptance rate is 58.1%
* Whereas, when the destination is Home, the acceptance rate is 36.4%
* Difference of 21.7%

Drivers respond to the coupon offer more frequently when there is no competing urgent destination.  In such contexts, the driver can afford the time to take an unplanned trip to the coffee house.

##### 5 - Passenger Type

* When the driver is travelling with Friends, the acceptance rate is nearly 60%
* When the driver is alone, the rate is only 43.8%
* Difference of 16.2%

When with friends, the detour may be reframed as a shared journey or an opportunity to hang out longer, than an inconvenience or hassle.  Drivers may be more willing to act on a deal when they know it creates shared value with a friend (e.g., “buy-one-get-one” or multiple drinks).

##### 6 - Age

* For drivers below 21, the acceptance rate is 69.7%
* For drivers 50 or over, the rate is only 41.7%
* Difference of 28.0%

Very young drivers had notably higher rates of acceptance.  It's possible that younger drivers, who may be just starting their careers or are still students, are more price sensitive and therefore more responsive to coupon offers.

### Next Step Recommendations

##### Propensity audience: 

* Build a Coffee House likelihood score (features above + recent visits) and allocate budget toward top deciles.

* Create a Student Loyalty Card to drive offers to younger drivers. Partner with student orgs/clubs to distribute coupons at events.

##### Contextual triggers:

* Time: Focus on 10AM (plus adjacent hours), test a late-morning block. Prioritize delivery when users aren’t headed somewhere time-critical (e.g., midday errands).

* Destination: Prefer “no urgent place” contexts; downweight evening commutes home. 

* Companions: Boost bids when with friends (proxied by weekend daytime, multi-device co-location, or car occupancy signals if available).

##### Offer design:

* Expiration: Standardize Coffee House coupons at same-day/24h rather than 2-hour windows.

* Creative: “Grab a coffee with friends” framing; “Good all day today” hook.
