## Help us build a decentralized marketplace

Thank you for taking the time to puruse this repository.  In this early stage, this is merely a platform for everyone to propose ideas and concepts.  It is open to the public, and everyone is welcome to participate.  Documenation will evolve and progress along side the project at large.

# Mission and Motivation

Publicly divorcing imperalistic marketplaces.  The purpose of this project is to create a publicly accessible and truly decentralized marketplace system.  This system could be deployed by anyone.  Anyone can improve upon it.  By leveraging the blockchain itself, every user would have access to every other market listing, regardless of what wallet or web3 site they use.  It is even conceivable that the entire marketplace could exist as a feature of the wallet applications themselves, eliminating all additional depencies on third parties.  More importantly it removes 100% of the leverage that the current marketplaces have today; thus creating a free enterprise, where feature enhancements would be highly encouraged.

The plan is not anywhere near its final state.  However, with Cardano having the greatest community of any blockchains, I have no doubt that many highly talented developers will be happy to provide their insights.  Assuming there is a shared interest in seeing this to fruition, there will be a fully vetted CIP proposed as the final state becomes more clear.

# Intial concepts

Release a policy key to the public with a very distinct purpose.  You will find the keysets below.  What you wont find is the skey from the stake reward account.  The reasons will be detailed.  The signing key, when paired with the script below allows anyone to mint and burn assets with the policy ID of e94d0e940b49c9cb2da421aedfca7557d7a4c09ec52724d2aff9b071.  The knee jerk response to this will be that if anyone can mint with this policy, then bad actors will likely bad act.  But in reality, they would only be hurting themselves, and costing themselves ada.  Because if used as proposed, only assets that are minted that meet certain criteria would be respected.  We would develop algorithmic matches, so that wallet applications could identify valie assets, and invalid assets.  And you'll see further in why it would be a total waste of time for someone to make junk assets.  The second concern is that people can create duplicate assets with changed metadata.  This is easily resolved by using the same mechanisms proposed in CIP-0027, to only respect the first mint of a given asset.

The way the system would work is by generating offer tokens, and acceptance tokens.  The final concepts for the token will require input from the community.  It could either be one mint for each potential trade.  Or each wallet would have a rolling token that updates their offers and accepts every time there is a change in status for a listing item.  Below is a sample of the steps of a transaction.

1) User wants to trade spacebud #1234 for 5000 ada
2) User interacts with the tool that establishes the settings needed.
3) The platform generates a transaction that partitions off spacebud #1234 in their wallet.  At the same time, this offer token is generated (or an existing one is updated).  Since this token is generated with the public policy, every marketplace participating now has access to this listing.

Note - I envision the token name deriving from either the parameters of this particular transaciton, or being part of a users first used wallet address.  I also envision the use of frankenaddresses for the siloed off utxo; but I will explain that further later.

4) Interested buyer would like to consumate purchase.
5) Buyer uses their preferred market interface that builds a single transaction that would require the spend of the sellers utxo, as well as their utxo that combined creates the desired transaction.  Another token would need to be generated on the buyer side (or again, their single trader token would be udpated).
6) Because of the data in the buyers token updated, the sellers wallet would notify them that it has identified that a buyer has signed their end of their offered trade.
7) Buyer would then sign the same transaction on their side after verifying that the transaction is what they intended.  I would anticipate wallet makers, and known good marketplaces to also put in their own validity checks to help protect the traders.

Other relavent details.

Since every wallet can build in this policy key, the wallets can auto detect bad tokens, and just burn them the next time a wallet is used.  This is the part that makes creating junk tokens a complete waste of time.  I may not even know you've dropped some on my wallet.  But the next time I use my wallet, I just reclaimed the ada you had bound to them.  So congrats on giving me free ada :)

Metadata could be hashed by a marketplace to show proof provinence, and added as additional field on a token.

Marketplaces are encouraged to bake a small fee in to each transaction.  I propose 1 ada for each side of the trade.  This will require marketplaces respecting instructions written in to a sellers trade data.  Since the seller will inevitably use the same site to finish the sale, that site can easily spot a bad market place trying to undercut or take their fee.  Speaking of which...

Reputation is easy to identify.  Since everything is done on chain, its easy to see who is making good transactions, and who isnt.  Bad actors can be blacklisted from marketplaces.  Hence the places that will do the best, are the ones that actually play by the rules.

Back to the stake key.  In the below is a stake key that was derived from this public wallet, and a rewards key.  The reason that was used, is it proves the provinence of this stake key.  But without the rewards skey, it has a very limited use.  One of those ideas is to hold pending sale items on a utxo that is a wallet address derived from the sellers wallet, and this public stake key.  This is well known as a Franken Address.  By doing this, it allows for a semi self funded solution for the continued building of this platform.  Assuming thousands or millions of assets available for sale at any one time, this rewards account would recieve a fair amount of ada.  And people who just want to donate can just create utxos in wallet using a frankenaddress.  If this idea is brought forward, I would like to see the ada distributed to those who have participated in the building of this in peretuity.  Since that is easily identifiable directly on this repository, that should be pretty straight forward.  And to ensure full transparency, and ensure this doesnt become centralized, I would provide this rewards key to Cardano Foundation.  Additionally this rewards account can be delegated from stake pool to stake pool as an additional benefit to pool operators that participate.  This could be done through community voting.  These tokens become very powerful when you start to think about it more.

staking wallet addresses
addr1qx3klssskv63uvnnwecqycklu7xtj6lkcmmxjsny5up9h6gy4egdjlztvr2v29r6nj05krdtnxzwk3t06nxkxsnh3c3s2rv97g
addr_test1qz3klssskv63uvnnwecqycklu7xtj6lkcmmxjsny5up9h6gy4egdjlztvr2v29r6nj05krdtnxzwk3t06nxkxsnh3c3sf439jh

staking address
stake1uyz2u5xe039kp4x9z3afe86tpk4enp8tg4hafntrgfmcugcpxu9al
stake_test1uqz2u5xe039kp4x9z3afe86tpk4enp8tg4hafntrgfmcugcxvk8ez

Public SKEY


{
    "type": "PaymentSigningKeyShelley_ed25519",
    "description": "Payment Signing Key",
    "cborHex": "58208c921ea0d2c60a818621d8c672d12304457b4e04c464431b10b83b88083e6fd7"
}

Policy ID

e94d0e940b49c9cb2da421aedfca7557d7a4c09ec52724d2aff9b071


Public Script

{"type": "sig", "keyHash": "a36fc210b3351e327376700262dfe78cb96bf6c6f6694264a7025be9"}


Enterprise wallets derived from skey
addr1vx3klssskv63uvnnwecqycklu7xtj6lkcmmxjsny5up9h6gzjxgu5
addr_test1vz3klssskv63uvnnwecqycklu7xtj6lkcmmxjsny5up9h6ge6j5n3

