# Roku Search feed

Channels participate in Roku Search by creating and submitting a search feed. The search feed is a single JSON file that includes the content metadata for a channel's video catalog. Content meta data includes the unique ID, title, description, duration, rating, language, artwork, and so on. Once the feed has been configured following this spec, it can be submitted to [Roku's feed validation tool](https://developer.roku.com/search/feed_validator), and the integration into Roku Search can then be completed. 

The Roku search feed includes the following key features:

- **One feed for all regions**. A single feed may contain region-specific content metadata and rating sources.

  

- **Content availabilty windows**. A feed may include availability windows for individual content items.

  

- **Variety of content**. The feed may contain the metadata for movies, television shows, and short-form content (for example, cooking videos, sports highlights, and so on). 

  

- **Multiple source IDs**. A single feed can contain both channel-specific and Gracenote content source IDs.

For more information on creating your feed, see the [Roku Search feed specification](https://developer.roku.com/docs/specs/search/search-feed.md#specifications).
