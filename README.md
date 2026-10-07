# SuperView

SuperView lets you write what you think will happen in the world, and turns that into a real portfolio you can track and invest in.

## Problem

Most people don't think in tickers. They think in ideas, like "AI companies will spend more on chips next year" or "there is going to be a water shortage in big cities". Everyone has views like this, but they mostly end up as a tweet or a message in a group chat and nobody ever checks if they were right.

If you actually want to invest in an idea like this, it is a lot of work. You have to figure out which companies benefit, how directly they benefit, how much to put in each one, and what would make you exit. Most people don't have the time for that, so they either skip it or buy one popular stock and hope for the best.

On the other side, social apps rank people by followers and likes, not by whether their calls made money.

## Solution

On SuperView you just write your view in one or two lines. Our agent does the research, picks the stocks, decides the weights and builds a basket for you. You can publish it, and then anyone can follow it, comment on it, copy it or put money behind it.

Every view is tracked live against a benchmark, so the leaderboard is based on actual performance and not on who is the loudest. If something changes later, the agent can suggest adding, trimming, exiting or rebalancing.

We also have a Masumi agent on Cardano. Anyone can hire it, give it a view, and it will do the full research and invest in the stocks on its own.

Video: https://www.loom.com/share/745798eb01d44429914ee12392922126

Website: https://superview.fun

## Ways to start a view

You can start in three ways:

- Write a normal market view in your own words.
- Switch to the memecoin desk and write a view about memecoins instead of stocks.
- Give an astrology chart (Vedic or Western). A lot of people already use astrology to think about markets, so we treat it like any other input. The agent reads the chart, writes a market prediction from it, and then builds a basket the same way.

## How it works for a user

1. Write your view, or paste an astrology chart.
2. Choose stocks or memecoins.
3. The agent researches and builds the basket. You can see what it is doing while it works.
4. Publish it. Now it has its own page with the thesis, holdings, comments and an invest button.
5. Track it. You can see the latest price, today's change, how much your money is worth and how the basket is doing against the S&P 500 (or against SOL for memecoins).
6. Follow people whose views are doing well, or copy their basket into your own portfolio.

You can start with paper money first, which fills against live prices. When you are ready, you can invest for real from your Solana wallet.

## Stocks and memecoins on Solana

All the markets in SuperView are on Solana.

For stocks, we use stock tokens on Solana. These track real listed companies like Nvidia or Apple, so the agent can pick from real companies and get live prices for them. Live investing uses USDC from your wallet, and you need a small amount of SOL for fees.

Memecoins are kept on a separate desk. Here the agent looks at launchpad coins instead of companies, and filters out coins that are too new or don't have enough liquidity. Memecoin baskets are compared against SOL instead of the S&P 500. The money in your memecoin portfolio is kept separate from your stock portfolio. Memecoins are very risky and can go to zero, so please keep that in mind.

## Masumi agent on Cardano

Our research agent is also listed as a Masumi agent on Cardano.

Anyone can hire it by paying on Cardano through Masumi and sending a view. The agent does the same research it does inside the app, builds the basket, and can invest in those stocks on Solana. It also sends back a short report with:

- what the view is really about
- the main assumptions
- what would prove the view wrong
- the stocks in the basket with their weights and the reason for each one

So the payment happens on Cardano, and the stocks are bought on Solana.

## How the agent works

We did not want one AI prompt to just pick some stocks. So the agent is set up like a small investment team, where each step has a different job.

**1. Understanding the view.** First the agent reads what you wrote and breaks it down. What is the actual reason this would make money, what time frame we are talking about, what assumptions it depends on, and what would prove it wrong. From this it comes up with 3 to 6 angles that can be invested in. For an astrology chart, this step reads the chart first and turns it into a market prediction. For memecoins, it looks at the narrative and the trend instead of a company's business.

**2. Finding candidates.** For stocks, it goes through the list of stock tokens available on Solana and also searches the web to find companies it might have missed. It only keeps companies that actually have a token we can buy. For memecoins, it goes through launchpad coins and skips the ones that look unsafe or too thin.

**3. Research on each name.** Every candidate gets its own research notes. Then each one is scored on how directly it benefits from the view, how much of its business is tied to it, how confident we are, and how risky it is. Each stock also gets a role in the basket: direct, indirect, related, or a hedge.

**4. Building the basket.** A portfolio step decides the weights. Usually it is 5 to 12 names plus some cash. There are limits so that one company or one sector does not take over the whole basket. If it cannot build a proper basket, it falls back to a simpler one instead of forcing it.

**5. Review.** A separate reviewer model checks the basket and can approve it or send it back for changes. This way the same model that picked the stocks is not the one approving them.

**6. Watching after publish.** Once it is live, the agent keeps an eye on it. Later it can say nothing has changed, or suggest a rebalance, adding a stock, trimming one, or exiting.

When the job comes from Masumi, the exact same steps run. The only difference is that the report goes back to the person who hired the agent.

## After you invest

On the view page you can see how much your money is worth now, your profit or loss in dollars and percent, and how each stock in the basket is doing. Right after you invest, it shows today's move. After that it shows the change since you invested.

The portfolio page shows the same numbers for everything you hold, along with the comparison to the benchmark.

Copying a view puts the same basket in your own portfolio. Comments stay on the view, so the discussion is about that specific idea. The leaderboard ranks views by how they actually performed.

## Note on Solana

We run on Solana Mainnet Beta with real stock tokens. Stock tokens are not available on Devnet, so there is no real market there for us to test this on.

We have not only read data from the chain. The full flow is built. Baskets are made from real stock token mints on mainnet, prices come from them, swaps go through Jupiter, tokens sit in normal SPL token accounts, and the wallet is a Privy wallet that handles login, wallet creation and signing. We did not deploy our own program because we did not need one. The stock market we are using already exists on mainnet, so we integrate the existing programs, Jupiter and the SPL token program (`TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`).

Since this is mainnet, sending real money for every test or demo does not make sense. That is why we built paper money as a proper feature. You pick an amount, it fills against live mainnet prices, and your value, profit and loss and benchmark all update exactly like a real investment. It is the same basket, the same prices and the same agent, just without sending a real transaction. When you want to invest for real, the same basket is signed and sent from your Privy wallet.
