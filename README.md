# QIAN 2.0：加密资产储备型稳定币

## 一、前言

### 1. 行业背景

  随着区块链技术和加密数字货币的流行，一种全新的货币形式已经出现。
  
  但是，由于加密数字货币的巨大波动性，使得其不能作为交易媒介，不能进行延期支付，也不能作为记账单位。基于对稳定性的需求，出现了以Tether（USDT）为代表的稳定币，发行规模已超过百亿美元。

  在加密世界，目前一共出现过三大类型的稳定币：法币托管型、非托管加密资产抵押型、算法稳定型。

  法币托管型，目前的代表币种为USDT、BUSD、HUSD、USDC、PAX、TUSD等，在稳定币当中占据最多的市场份额。

  加密资产抵押型，目前的代表币种为MakerDAO推出的DAI，此类稳定币市场占比次于法币型，由于去中心化程度较高，受到了开源社区的拥护，发展迅速。

  算法稳定型，代表项目为Ampleforth，其稳定性调节机制建立在对总供应数量的自动化调节上，由于机制简陋，事实上无法维持币价稳定，遭到较多的质疑，市场份额目前很低。

### 2. 问题陈述

  稳定币DAI在设计上借鉴了BitShares里的BitUSD，以加密资产作为抵押物，为稳定币的内在价值作担保。无论是BitUSD还是DAI，都是处于试验阶段的产品，其内在机制尚有许多值得改进之处。

  以最为核心的发行机制为例，美元的发行，实行“发行抵押”制度，各联邦储备银行在获得新增的美元时，必须向美联储提供等于或大于其发行流通的货币数量100%的合格抵押品，以及附加担保品。其中大部分抵押品是联邦储备银行拥有的美国国债，此外还有黄金证券、合格的商业票据、抵押票据、银行承兑票据、合格的州及地方政府的债券。

  所有使用中的美元现金，全都由美联储发行，美元实际是美联储创造的一种联邦储备券，并且在发行时拥有充分的担保，担保品主要为美国国债，国债的价值又由美国政府的信用支撑，美元的发行是以美国政府的信用为担保。

  对于美国政府而言，为了发行美元所需要的成本仅仅是每年2%左右的国债利息，美元的发行，不需要发行方（美联储）再提前准备任何资产，否则，发行美元的成本将大大增加，美元对美国经济活动的刺激能力也将变弱。

  基于MakerDAO团队的国籍背景，他们在产品设计之初明显参考了美元的货币发行机制，DAI实际上是MakerDAO系统的抵押券。而DAI的发行，依赖于CDP，CDP的持有人不仅需要提前花费真金白银购入ETH等加密资产，还需要背负DAI的稳定费。这相当于发行美元既要美国政府提前买入黄金，而且还要凭借黄金储备才能发行国债，付出的成本大增。无论怎么分析，对于货币发行人而言都是赔本的生意，这种设计从根本上制约了 DAI 的发行量。

  因此，如果不从底层设计进行突破，类似于DAI这样的稳定币，其供应量不可能获得巨量增长，在法币托管型稳定币的挤压下，其影响也将逐渐式微，最终局限在一个小众的圈子里成为一种另类资产，或者被机制更加合理的加密资产抵押型稳定币所替代。

### 3. 港币的发行机制

  美元是通过政府信用发行货币的典型，只有具备强大实力和持续信用记录，能够按期归还国债本金和利息的政府，才能保证这套货币发行机制的持续。另一种国际上主流的货币发行机制，是以其他国家的法定货币（外汇）作为本国/地区货币发行的担保。例如，某种货币通过和美元保持固定汇率，进而间接保持自身币值稳定，此为联系汇率制。在联系汇率制里，必须以等额甚至超额的美元资产作为发行担保，方能保持该种货币的价格稳定。采用联系汇率制的法定货币中具有代表性，我们也可能会接触到的，就是港币。
  
  港币发行制度的特色之一是以至少100%的美元外汇作为其发行准备，具体而言，发钞银行以固定汇率向香港政府管理的外汇基金交付等值美元，换取负债证明书，然后发行与所交付美元等值的港币。如果发钞银行想减少港币发行量，就按照固定比率向外汇基金提交港币和负债证明书，换回等值的美元。
  
  港币发行时基于外汇进行了超额抵押，根据2020年1月的报告数据，香港的外汇储备在2020年1月1日达到445,545.0百万（4455.45亿）美元，与之对应，发行的港币M1在2020年1月1日达到206,626.864百万（2066.26864亿）美元。外汇储备对基础货币的比例达到了2倍以上，港币因此具有非常高的安全垫。
  
  如果市场上的美元需求上升，港币贬值，例如市场价变为1:7.9，发钞银行就会用1美元在市场上购买7.9港币，然后用7.8港币从外汇基金赎回1美元，从中获得0.1港币的差价，完成套利。在这个交易过程中，港币被回收，市场上流通的港币数量减少、需求上升，汇率也将相应上升。
  
  如果市场上的港币需求上升，例如变为1:7.7，发钞银行将用7.7港币购买1美元，然后用1美元从外汇基金购买7.8港币（准确说是7.8港币的发行权），从中获得0.1港币的差价。这个交易过程中，美元数量减少、港币数量增加、需求减少、汇率回落。
  
  上述过程描绘了港币的联系汇率机制，正因为港币以美元作为担保货币，保证了最广泛的接受度，这对于香港向全世界保持经济开放，从而成为亚洲的金融中心起到了根本的推动作用。

## 二、QIAN 2.0介绍

### 1. QIAN 的创造依据

  港币发行的核心，就是银行在持有外汇资产以后，可以零成本的将外汇资产抵押给香港政府，换取货币发行的权力；而香港政府向银行赎回港币，也不需要支付额外的成本，双方只需要规定事先约定好的兑换比例即可。

  拥有了这套最小摩擦机制，才能保证港币和美元之间进行无缝转换，从而激发港币的发行，带动整个香港地区经济的持续繁荣。
  
  真正可能取得成功的加密资产抵押型稳定币，应该参考港币的发行机制，采用联系汇率制进行设计，由于加密资产具备货币属性但又价格波动较大，因此需要在联系汇率制的基础上做适当的调整和风控设计，用代币互换的理念设计新型的稳定币。基于这些设计原则，我们设计了QIAN stablecoin系统，以打造一套可以真正被广泛使用的非托管型加密稳定币发行、回收、管理系统。

### 2. QIAN 的重要概念

  QIAN：同“乾”和“钱”。在《易经》当中，乾卦代表天，代表宇宙万物运转的规律，是最崇高的正向能量和精神。乾卦代表阳气多，阳气强，阳气盛，谓之健。天行健，可以不停的往前走往外发扬。天这种创造力是因为它永远不停息，乾很刚健，正象征着中华民族蓬勃向上的发展。遵循这个重要的涵义，我们将首个采用代币互换制的加密资产储备型稳定币命名为 QIAN。
  
  KUN：同“坤”，坤象征大地，承载万物，人们基于土地进行劳动，耕耘，坤象征着人之治。KUN是QIAN 稳定币协议的治理代币，用于对QIAN生态治理投票和维持QIAN价格稳定。
  
  QUSD：QIAN系统发行的第一种稳定币，以美元的汇率作为其定价标准，通过一系列稳定性调节机制，维持其币价稳定。未来，QIAN系统还将根据用户的需求，发行对应不同国家法定货币汇率的各种稳定币，例如QEUR、QHKD等。
  
### 3. QIAN 的设计理念

  QIAN系列稳定币的发行权，属于每一个加密资产持有者。
  
  参考港币的联系汇率制度，QIAN的稳定币将被视为智能合约对加密资产/代币持有人的代币交换证明。持有美元的银行，就像持有 ETH 等加密资产和代币的用户；而发行港币的香港政府，就类似于控制 QIAN 系列稳定币发行和回收的智能合约系统。
  
  持有加密资产/代币的用户，只需要将超额的加密资产/代币锁定到QIAN的智能合约，就可以获得以各国法定货币的价格为参考标准的QIAN系列稳定币，QIAN系列稳定币是一种代币符号，在法律意义上不具备法偿性，不是法定数字货币，不可视作货币资产，仅是DeFi系统的一种价值参考物。
  
  QIAN的生成和持有不需要支付任何利息，这不同于MakerDAO等稳定币的债仓机制，而是一种货币互换。稳定币 QIAN 被视为智能合约对加密资产持有人的货币交换证明，我们将这一机制下的智能合约命名为 CSA（即 Currency Swap Agreement，货币互换协议）。持有 CSA 不同于 CDP，无需支付利息，这样一来，QIAN 的 CSA 就有了长期被持有的可能。

#### 3.1 固定汇率机制
  
  为了维持 QIAN 的价格恒定，熨平QIAN代币的价格波动，我们将围绕 QIAN 打造一个可供套利者交易的市场，通过市场行为来控制其价格稳定。QIAN 将建立一套完善的交易套利机制，在 Uniswap、Curve 等去中心化交易平台和部分的中心化交易所进行应用。与外部协议进行联动，通过市场调节 QIAN 系列稳定币的价格，以保持QIAN稳定币对法定货币汇率的稳定。
  
  在特定的条件下，例如当 QIAN 系统的整体储备资产低于一定水平，导致 QIAN 系列稳定币的市场价格低于其面值，且持续一段时间没有恢复。此时，非 CSA 持有者可通过 QIAN 2.0 的智能合约，使用 QIAN 系列稳定币从系统中按面值赎回对应于市场价格的加密资产。在二级市场套利之外，有了第二条套利路径。围绕“QIAN系列稳定币/法定货币”的套利操作，将使 CSA 的开启/关闭得到有效的调节。

#### 3.2 负利率激励

  当QIAN系列稳定币对法定货币升值时，意味着整个体系QIAN的供应量不足，单位QIAN系列稳定币能够换回更多的资产，此时需要促进更多的CSA生成，让QIAN系统的供应量回归到正常范围，进而促进币价的回归。为了实现这一目的，我们通过引入负利率来进一步促进QIAN系列稳定币汇率的调节。
  
  负利率是调整QIAN稳定币供应量的一种机制，为了维持 QIAN 生态的发展和稳定，锁定加密资产铸造 QIAN 系列稳定币在默认情况下不会产生利息。当系统认为需要激励铸币者以提升 QIAN 系列稳定币的流通量时，系统会支付利息给新创立CSA的用户，支付的利息以KUN代币的价值进行计算，发放的利息也是KUN。负利率相关的决策在QIAN 2.0上线初期将通过社区治理进行，最终将过渡到由自动化算法决定。

#### 3.3 持有CSA无需成本

  作为流动性提供者，持有QIAN的CSA不需要支付任何利息，相反有可能获得来自于智能合约的激励作为额外收入，这将刺激用户长期持有QIAN的CSA，使QIAN系列稳定币有了被用于各种DeFi活动的可能。无需持有成本，QIAN系列稳定币才有可能真正的参与并促进开放金融（DeFi）生态的发展过程，与同样无需持有成本的法币担保型稳定币共同发展，服务不同需求的用户。

#### 3.4 促进ETH等加密资产的使用
  
  QIAN 2.0系统将支持多种加密资产与智能合约进行代币互换，用户持有ETH等加密资产，锁定到QIAN的智能合约后，可以用换得的QIAN进行各类交易、投资活动。无需抵押利息，减轻了加密资产持有人的经济负担。
  
  结合Compound、AAVE、ForTube等各类DeFi货币市场协议，以及日益成熟的去中心化交易类协议（Uniswap、Curve、Balancer等），用户将会通过QIAN获得超额的投资回报，也能强化ETH等加密数字货币的资产属性，促进更多的人持有加密资产。

#### 3.5 结合闪电贷等新技术，进一步创造收益

  目前已知闪电贷（Flash loan）是一项安全的技术，任何拥有资产的智能合约，都可以选择对外提供闪电贷服务，通过收取一定量的借贷利息，可以利用自身资产增加更多的收益。目前已经在以太坊DeFi生态中出现了闪电贷的聚合类工具，通过将支持闪电贷的智能合约的流量进行聚合，可提供更强大的闪电贷服务。

  QIAN的智能合约将支持闪电贷，锁定在QIAN智能合约里的加密资产可以获得额外的收益，QIAN stablecoin governance committee将定期的用获得的收益在市场上买入KUN代币，KUN作为QIAN系统收益的价值贮藏载体，将被锁入保存QIAN系统收益的智能合约。

#### 3.6 自带使用场景，稳步扩大市场

  任何一个稳定币的运作团队，都需要清晰的回答这几个问题：谁是稳定币的用户，稳定币的使用场景有哪些，如何扩大稳定币的市场占有率？
  
  QIAN 2.0 作为加密资产储备型稳定币的代表项目，拥有清晰的答案：
  
   + 首先，持有QIAN的CSA没有利息成本，能够覆盖所有加密资产用户。
    
   + 其次，由于没有长期持币成本，QIAN将有可能扩展到DeFi的所有使用场景，被各种DeFi协议所支持。
    
   + 第三，QIAN 2.0的所有权属于KUN的全体持币用户，正式上线以后，将通过广大的KUN用户群体共同努力，与开放金融各参与方积极合作，逐步扩大市场占有率。


#### 3.7 风险控制

  在 QIAN 的设计中，我们遵循如下的风险管理规则：
  
  首先，QIAN 2.0 秉持超额储备原则，用户在使用 ETH 等加密资产生成 QIAN系列稳定币时，需要满足一定比例的启动充足率，锁定加密资产的价值与生成稳定币的价值比例至少要大于120%。
  
  其次，为了增加CSA内锁定资产的安全性，避免在极端行情下产生爆仓，同时兼顾加密资产的利用率，QIAN 2.0将根据加密资产市场价格的变化速度，引入波动率因子，调控CSA的资产锁定倍数。
  
  当价格进行单边上涨或下跌时，波动率上升，系统将上调CSA的启动锁仓比例。在市场较为平稳的时期，波动率下降，系统将下调CSA的启动锁仓比例。这种设计将有效的减轻市场波动对CSA锁仓资产的影响，鼓励用户在市场平稳的状态下进行CSA锁仓，增加锁仓资产的安全性。
  
  第三，当市场行情暴跌时，用户的CSA充足率会下降，在下降过程中，CSA有预警状态和冻结状态两种变化。

  例如，某用户持有ETH的CSA，当其储备资产充足率下降到150%（ETH的预警线）附近，QIAN系统将会提示用户补仓。 此时，如果行情继续暴跌，用户来不及进行补仓，CSA的充足率继续下降，当低于120%以下时，智能合约将会冻结用户的CSA，直到用户补充锁定资产到安全水平以上才进行解冻。用户在补充锁定资产之前，将不能通过自己的地址发起对于锁定物的赎回。
  
  由于QIAN 2.0支持多种加密资产锁定，用户手头可能持有不同资产的CSA，不同资产之间的内在风险不同，因此会有不同的风险控制线，具体的控制标准（预警线、冻结线的具体数值），将由社区进行充分讨论之后决定。
  
  第四，处于冻结状态的 CSA 可能被清算，允许非 CSA 持有者用 QIAN 系列稳定币按照所有处于冻结状态 CSA 所生成的稳定币数值赎回冻结合约当中的资产，这部分内容将在后续平滑套利机制章节详细阐述。
  
  此外，QIAN 2.0版本将会保持在1.0版本当中设计的全局债务拍卖机制。极端行情之下，QIAN系统内某几种或全部储备资产的充足率可能低于100%，导致QIAN系列稳定币的内在价值支撑不足。如果此时CSA持有人普遍没有意愿补充锁定物，而且底层储备资产的市场价格在一段时间内都没有恢复，这将会在QIAN系统形成储备缺口（债务）。在这种情况下，系统会在整体储备充足率持续低于某一水平，且经过一定的观察期之后，启动全局债务拍卖。在全局债务拍卖里，系统将解冻由QIAN stablecoin governance committee所提供的治理代币KUN并对外拍卖，拍卖所得的收益将用于弥补整个系统的储备资产充足率。相当于QIAN stablecoin governance committee和全体KUN的持币人一起，会为QIAN系统做最终兜底。


#### 3.8 QIAN 2.0的设计优势总结

<b> 总结而言，QIAN 的设计优势如下：</b>

|  | <b>QIAN 2.0</b> | <b>DAI</b> |
| ------ | ------ | ------ |
| <b>发行机制</b> | <b>联系汇率制</b> | 抵押借贷制 |
| <b>CDP持有成本</b> | <b>无成本，潜在正收益</b> | 成本中到高 |
| <b>CDP持有风险</b> | <b>中、低风险</b> | 中、高风险 |
| <b>抗极端行情能力</b> | <b>强，待检验</b> | 弱，已暴露 |
| <b>抵押资产是否有收益</b> | <b>正收益</b> | 负收益 |
| <b>对新技术的支持</b> | <b>强</b> | 待观察 |
| <b>生态支持</b> | <b>完善中</b> | 较完善 |
| <b>是否有最终购买方</b> | <b>有，KUN持有人</b> | 有，MKR持有人 |
| <b>目标市场</b> | <b>DeFi、实体经济中的跨境支付、消费支付、资产交易、借贷活动等各类经济活动</b> | 主要局限于DeFi，正进行扩展 |
| <b>汇率对标的法定货币</b> | <b>人民币</b> | 美元 |


## 三、锁定物管理

### 1. 加密资产核心配置参数

  QIAN 系列稳定币由用户向智能合约锁定加密资产生成，初期的底层资产将以ETH、BTC代币、各类加密稳定币等加密数字货币为主，待系统稳定运作一定时期后，将考虑纳入具备共识的线上线下资产NFT token 等作为发行抵押物。考虑到 token 类资产的高波动性和高相关性，将要求超额储备各类资产。
  
  对于每一种加密资产，系统配置的核心参数包括：

  + **市场价格波动率Voli**：由于加密资产的高频交易特性，QIAN 2.0系统将借鉴目前国际市场上常见的，反映期权价格波动的指标RV（Realized Volatility），定义加密资产i的波动率为Voli。在系统上线初期，Voli将根据预言机的报价间隔进行更新，稳定币和期权的概念不同，通过近期的已实现波动率即可有效调控底层资产的风险，因此Voli不涉及对未来波动率的预测。

  + 启动充足率Qi,0：受到每种加密资产市场价格波动的影响，Qi,0处于动态的变化中，在QIAN系统上线初期，Qi,0将根据预言机的报价周期进行更新；
  
  + 当前资产充足率Qi,t：；
   
  + 最低充足率Qi,min：资产i的CSA充足率低于某个比例时将触发冻结；
   
  + 预警充足率Qi,alarm：，CSA低于某个比例时将触发预警，提示用户为了保持健康的充足率，需要向CSA补充更多储备资产，但用户如果不补充，也能正常进行CSA的赎回操作；
   
  + 最高铸币量：指该类加密资产在系统中所能铸造QUSD的最大量；
   
   其中，为当前锁定的加密资产i总体价值，报价来自预言机，定期更新。
   
   对于特定的加密资产i，设其可铸币量为H，则有 ![image](https://github.com/thefortube/QIAN/blob/Dev/svg/svg01.latex.svg), 其中，*__Pledged(i)__* 为当前锁定的加密资产数量；*__Price(i)__* 为当前加密资产的市场价格（来自预言机）。
  

### 2. 系统整体核心配置参数

  对于系统整体，核心参数包括：

  + 全局资产充足率Qtotal：
  
  + 全局最低充足率Qmin：初始阶段，要求Qmin≥90%，后续会通过社区治理流程进行调整。
  
  + 债务拍卖观察时间Tauction：当Qmin出现后，距离全局债务拍卖开始的时间。


### 3. 加密资产组合管理

  为了避免 QIAN 系列稳定币（例如QUSD）的价格波动，分散风险，提升稳定性，QIAN 系统将从主流加密数字货币和 token 化资产中选择储备物，选择的指标包括但不限于：资产类型、市值、流动性、波动率、发行主体、发行地区等。

  由于 QIAN 是一个去中心化的系统，人人皆可自由参与铸造 QIAN 系列稳定币。因此，QIAN 系统的加密资产组合管理是一个弹性较大的组合管理策略，系统并不刻意维持各加密资产在系统中所占的比率。但是，如前文所述，系统将为不同加密资产i设置最大铸币量，该参数与加密资产i的CSA开启所需要的充足率相关，低波动性加密资产的最大铸币量更高。

## 四、稳定性管理

### 1. 价格波动缓冲机制

### 2. 加密资产平滑套利清算机制

  QIAN 系统将根据 VolR 的值决定是否开启套利机制，系统鼓励在市场波动较低的情况下进行清算，以减缓市场短期恐慌情绪对 QIAN 系统稳定性的冲击。
  
  在任意时间t(i)，对于充足率Qi,t，QIAN系统会存在以下几种CSA状态：

  + 正常合同CSA(normal)，Qi,t＞Qi,alarm
  + 预警合同CSA(alarm)，Qi,min＜Qi,t≤Qi,alarm；
  + 冻结合同CSA(frozen)，Qi,t≤Qi,min；
  
  对于不持有CSA(frozen)的套利者，其赎回行为可能会导致CSA持有人的锁定资产减少。为了兼顾公平和效率，对于平滑套利清算的参与者而言，其在时刻t(i)可赎回资产的来源，将被限制在CSA(frozen)。
  
  在套利过程中，套利者将从储备资产 i 的整体冻结资产当中套利，具体来说，假设在 t 时刻，QIAN 系统有100个处于冻结状态的 CSA，这些 CSA 一共生成了100,000 QUSD。此时，任意一个或n个套利者可以用不大于100,000 QUSD 的清算资金，按照出资额大小，从清算合约里获得部分/全部冻结资产。在清算过程里，持有 CSA(frozen) 的所有用户都会按其被冻结资产占冻结 CSA 内总资产的比例分担损失。
  
  所有处于CSA(frozen)中的储备资产都可以被套利者赎回，为了使自己不受损失，CSA(frozen)的持有人必须抢先补充自己CSA里的储备资产，使其脱离冻结状态。无论是套利者的赎回操作还是CSA(frozen)持有人的补充锁仓，都能够有效的提升QUSD的资产储备充足率，让 QUSD 在储备资产不足的情况下尽快价值回归。
  
  这种清算机制的设计既可以促使所有 CSA(frozen) 的持有者补充储备资产，也平滑了冻结资产的清算速度和数量，尽可能的减缓和减少单个用户所受的损失，因此，我们将这一机制命名为平滑套利清算。
  
  当 QIAN 系统支持多种加密资产时，平滑套利清算机制将变得复杂。理论上，套利者可赎回系统中的任何一种符合清算条件的储备资产，各储备资产之间不存在清算的先后顺序。当套利者赎回加密资产时，系统实时动态呈现各加密资产的可赎回量。套利者在可赎回量的范围内赎回加密资产，将不会大幅改变整个系统加密资产的分布情况。
  
  各种加密资产的可赎回量始终处在动态变化中，当质押资产i已经达到最大赎回比例Ri后，客观上提升了系统的整体储备充足率，此时质押资产i的套利操作受到最大赎回量的影响而暂停，由于QIAN是一个多抵押系统，对其他质押资产的套利活动仍将继续。

#### 3. 债务拍卖

  在极端情况下，系统的全局资产充足率Qtotal可能不足100%，如果市场环境持续低迷，此时的清算套利过程将可能会不顺利，套利者的套利意愿不足。此时，系统内的储备资产价值不足，将产生整体债务。为了维持QIAN系统的内在价值，系统将解锁（unlock）治理代币 KUN 并通过拍卖的形式补齐整体各储备资产的差额，让整体充足率回到安全线以上，恢复 QUSD 在极端行情下的内在价值。

  对于债务拍卖的参与者而言，吸引他们参与债务拍卖的原因，是被解锁的 KUN 将以低于市场价的形式折价进行拍卖，在 QIAN 的债务拍卖中，会引入最大折价率 *__Δr__* 。*__Δr__* 的初始值设置为70%，具体数值将由社区充分讨论后通过投票进行修改。参与债务拍卖的 KUN 总量为：

![image](https://github.com/thefortube/QIAN/blob/Dev/svg/svg04.latex.svg)

KUN 的拍卖中，起拍价：

![image](https://github.com/thefortube/QIAN/blob/Dev/svg/svg05.latex.svg)

拍卖参与者以资产 **i** 作为报价和结算标的，最终成交价 *__i(final)__* 为：

![image](https://github.com/thefortube/QIAN/blob/Dev/svg/svg06.latex.svg)

拍卖所得的资产 **i** 将用于弥补系统债务差额，若有剩余，则会锁定到拍卖盈余合约，以备未来所需。


#### 4. 全局清算

  虽然我们长期看好加密资产的发展，但是我们也必须要正视这样的一个现状：加密资产仍然处于整体发展的早期，市场暴涨暴跌时常出现，在过往的市场记录中也曾出现过长达数年的熊市。
  
  虽然QIAN稳定币系统有着一系列的稳定机制，但是仍然有可能在发生市场极端行情并且市场长期低迷的情况下，即使通过债务拍卖也仍然无法弥补整个系统的储备资产充足率。如果发生了这种情况且持续一段时间，将意味着整个QIAN稳定币系统丧失了内在价值的支撑，我们在这种情况下，将通过社区治理的流程，探讨是否进行全局清算并且关闭QIAN稳定币系统。一旦社区治理通过了QIAN稳定币系统的关闭议案，则将会启动全局清算。

  在全局清算状态下，QIAN稳定币系统将会首先冻结所有CSA，关闭CSA的生成功能，其次关闭预言机喂价，并且以最后一次预言机喂价的价格作为系统全局清算的参考报价。此时，系统状态再次发生改变，持有CSA(normal)的用户将能够优先向合约赎回自己的锁定资产，系统将处理这部分用户的资产赎回操作。在CSA(normal)的持有用户赎回资产完成之后，系统内如果仍然存在储备资产的剩余，则将允许CSA(alarm)的持有用户进行赎回。
  
  在全局清算状态下，用户是否能够拿回全部锁定资产，不受到损失，这是不确定的。能够全额赎回锁定资产的概率，依次为CSA(normal)＞CSA(alarm)，不同的底层储备资产的数量、市价等因素会对赎回成功的概率形成综合影响。


## 五、外部系统

### 1. 预言机

  系统需要实时获取外部价格以监控质押率的变化，以便及时启动锁仓，控制风险。预言机为系统提供及时的外部价格信息，包括稳定币QUSD、治理代币KUN及储备代币，以及充足率Qi等关键参数。

  在没有成熟的去中心化预言机解决方案时，系统将维护一个喂价地址白名单，该白名单由社区治理投票新增或去除。每个喂价都包含价格信息和价格有效期，系统从所有有效喂价中计算出中位值作为最终价格。在有了KUN持币人普遍认可的预言机方案之后，系统将会切换到对应的去中心化预言机，以保证喂价机制的公平、公正、公开、透明。

### 2.交易平台

  当储备资产价格下跌迅速时，系统可能面临暂时性的储备资产充足率不足，根据负利率机制，系统可能会向用户支付利息；在日常的运作过程中，QIAN系统也可能会通过闪电贷获得利息收入。因此，QIAN系统在运作过程中可能出现盈余或者亏损，这时，就需要引入外部交易平台，实现 QUSD、KUN 和储备资产之间的竞价交易。

## 六、系统治理

### 1. 系统参与方

  QIAN系统的主要参与者包括 QIAN 系列稳定币铸造者，QIAN 系列稳定币持有者及治理代币 KUN 的持有者。系统治理的目的在于平衡所有参与者的利益关系，在一定权衡和取舍的基础上，维持系统的稳定和持续健康发展。
  
  QIAN 系列稳定币的铸造者在系统中主要承担的风险是储备资产价格下跌，系统锁定后导致的赎回风险，享受的利益包括获得流动性、价值贮藏、风险对冲等功能。基于对行业中类似方案的研究，我们认为，在合理的风险范围内，QIAN 系列稳定币的铸造应该是被鼓励的，这有利于 QIAN 系统的发展，所以我们设计了可调整的利息机制。
  
  QIAN 系列稳定币持有者的核心诉求在于其汇率稳定性，因此我们设计了汇率稳定调节机制。
  
### 2. KUN治理代币

  KUN 持有者将是整个系统最后收益或风险的承担者，平台的管理是通过 KUN 持有者发起提案，进行投票进行的。
  
  KUN的总量为1200万枚，所有的KUN都将通过收益耕作、流动性挖矿、治理锁仓等特定的形式分发给QIAN系统的参与者，KUN 100%属于社区，无团队、无私募、无预挖。
  
  KUN的具体分发方式将由QIAN stablecoin governance committee制定并公布在QIAN的官网及治理论坛。如果在项目发展中需要调节KUN的分发方案，可通过投票方式进行。


### 3. 治理投票


被投票选中的提案可以修改 QIAN 平台的内部管理变量，这些变量包括但不限于：
  
  + 增加新的储备资产
  + 选择可信任的预言机
  + 调整利息
  + 调整闪电贷利率
  + 风险参数：每种储备资产的债务上限、初始锁定比例、可赎回上限、预警线等。


## 参考文献
[1] Wikipedia. Federal Reserve [EB/OL].
https://en.wikipedia.org/wiki/Federal_Reserve

[2] Wikipedia. United States Treasury security [EB/OL].
https://en.wikipedia.org/wiki/United_States_Treasury_security

[3] Fedreal Reserve Bank of New York. How Currency Gets into Circulation [EB/OL].
https://www.newyorkfed.org/aboutthefed/fedpoint/fed01.html

[4] Wikipedia. 香港外汇基金 [EB/OL].
https://zh.wikipedia.org/wiki/香港外匯基金

[5] MBA智库·百科. 货币发行制度 [EB/OL].
https://wiki.mbalib.com/wiki/货币发行制度

[6] 香港金融管理局. 强方兑换保证 [EB/OL].
https://www.hkma.gov.hk/gb_chi/news-and-media/insight/2005/05/20050519

[7] 香港金融管理局. 外汇基金资产负债表摘要及货币发行局帐目 [EB/OL].
https://www.hkma.gov.hk/gb_chi/news-and-media/press-releases/2018/04/20180430-4/

[8] 潘攀（北京大学金融法研究中心）. 港币的发行及其稳定机制 [J]. 金融法苑, 1999, 14（总第二十六期）: 52页

[9] 朱孟楠. 香港外汇基金的发展及投资策略的选择 [J]. 国际经济合作, 1997, No.6: 39~42页

[10] Prashant Bhayani & 谭慧敏（香港首席投资策略师）. 为何我们不担心港币联系汇率制度 [EB/OL].
https://wealthmanagement.bnpparibas/asia/cns/news/hkd-peg.html

[11] 瞿新荣. 美联储重启扩表，美元发行的逻辑与油价 [EB/OL].
https://www.guancha.cn/QuXinRong/2019_10_13_521093_s.shtml

[12] DAppTotal. 稳定币 [EB/OL].
https://dapptotal.com/stablecoins

[13] CEIC. 中国香港特别行政区 外汇储备 [EB/OL].
https://www.ceicdata.com/zh-hans/indicator/hong-kong/foreign-exchange-reserves

[14] CEIC. 中国香港特别行政区 货币供应M1 [EB/OL].
https://www.ceicdata.com/zh-hans/indicator/hong-kong/money-supply-m1

[15] RealVol Indices and Instruments. RealVol Daily Formula (Realized Volatility Formulas) [EB/OL].
https://www.realvol.com/VolFormula.htm

[16] RealVol Indices and Instruments. RealVol Real-Time Formula (Realized Volatility Formulas) [EB/OL].
https://www.realvol.com/VolatilityFormula2.html
