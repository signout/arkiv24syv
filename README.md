# arkiv24syv
This can (when finished) create a mirror of 24syv podcast archive

URL for the archive is https://arkiv.radio24syv.dk/  
URL for a specific podcast is https://arkiv.radio24syv.dk/audiopodcast/channel/4466232  
URL for all podcasts as RSS can be found at https://arkiv.radio24syv.dk/rss it gives 100 results per page and the rest are on sequentially numbered URLs like http://arkiv.radio24syv.dk/rss?p=2



### DB layout

```sql
sqlite3 arkiv24syv.db
CREATE TABLE IF NOT EXISTS items (
  x INTEGER PRIMARY KEY ASC,
  entirepost,
  contenturl,
  filesize,
  title,
  link,
  description,
  guid,
  pubdate,
  duration
);
PRAGMA table_info(items);
```

### RSS entry

..looks like
```xml
<item>
  <enclosure url="https://arkiv.radio24syv.dk/49543331/54202478/dfc90ad8eaf93453562ed3961e565a5f/video_medium/nyheder-1000-28-07-2019-video.mp4?source=podcast" type="video/mp4" length="3550177"/>
  <title>Nyheder 10.00 28-07-2019</title>
  <link>https://arkiv.radio24syv.dk/photo/54202478/nyheder-1000-28-07-2019</link>
  <description>
    <p>
      <p>Nyheder fra Radio24syv</p>
      <ul>
        <li>Kriminalitetsnævn afgør flest sager om børn under 15 år</li>
        <li>Vrede guatemalanere kalder asylaftale med USA umoralsk</li>
        <li>Voldsom stigning i antallet af indbrud mod tandlægeklinikker</li>
        <li>Hvis for mange danskere anskaffer sig en elbil...</li>
        <li>Lars Bak parkerer cyklen efter sæsonen</li>
      </ul>
    </p>
    <p>
      <a href="https://arkiv.radio24syv.dk/photo/54202478/nyheder-1000-28-07-2019">
        <img src="https://arkiv.radio24syv.dk/49543331/54202478/dfc90ad8eaf93453562ed3961e565a5f/standard/download-thumbnail.jpg" width="1400" height="1400"/>
      </a>
    </p>
  </description>
  <guid>https://arkiv.radio24syv.dk/photo/54202478</guid>
  <pubDate>Sun, 28 Jul 2019 10:00:00 GMT</pubDate>
  <itunes:summary>
    Nyheder fra Radio24syv
Kriminalitetsnævn afgør flest sager om børn under 15 årVrede guatemalanere kalder asylaftale med USA umoralskVoldsom stigning i antallet af indbrud mod tandlægeklinikkerHvis for mange danskere anskaffer sig en elbil...Lars Bak parkerer cyklen efter sæsonen
  </itunes:summary>
  <itunes:subtitle>
    Nyheder fra Radio24syv
Kriminalitetsnævn afgør flest sager om børn under 15 årVrede guatemalanere kalder asylaftale med USA umoralskVoldsom stigning i antallet af indbrud mod tandlægeklinikkerHvis for mange danskere anskaffer sig en elbil...Lars...
  </itunes:subtitle>
  <itunes:author>Radio24syv</itunes:author>
  <itunes:duration>04:59</itunes:duration>
  <itunes:image href="https://arkiv.radio24syv.dk/49543331/54202478/dfc90ad8eaf93453562ed3961e565a5f/standard/download-thumbnail.jpg/thumbnail.jpg"/>
</item>
```

Occationally it seems like they insert items other than at the top of the list. Maybe I should load two or three pages or maybe sift through all of them from time to time.

Looks like this  
```
Inserted 54754594
Inserted 54753152
Inserted 54751787
Inserted 54591692
Inserted 54754669
Inserted 54750313
Inserted 54748965
Inserted 54750298
Inserted 54747800
Inserted 54748950
Inserted 54746733
Inserted 54747794
Inserted 54745667
Skipped 54744568
Inserted 54746811
Skipped 54743553
Skipped 54742558
Skipped 54741514
Skipped 54740278
```
