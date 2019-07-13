#Harry Potter

#1A / 1B
hp<-read_html("http://www.imdb.com/title/tt1201607/fullcredits?ref_=tt_ql_1")
hp_table<-html_nodes(hp,"table")
derp<-html_table(hp_table)

# Find the right table
derp[1]

#1C - Cleaning
a<-data.frame(derp[3])
names(a) <- c("Blank", "Actor", "Blank2","Character")
df<-a[2:length(a$Actor),c("Actor", "Character")]
df$Character[10] <- "Griphook / Professor Filius Flitwick"

# 1D -Edit The Cast List
b<-df %>%
  slice(-92) %>% # Removes the row that is just noting the rest is alphabetical
  separate(Actor, into=c("FirstNames", "Surname"), sep="[ ](?=[^ ]+$)") # Separates the Last Name

#1E 
head(b, 10)


#SportsBall

sb<-read_html("http://www.espn.com/nba/team/stats/_/name/sa/san-antonio-spurs")
sb_table<-html_nodes(sb,"table")
sb_dfs<-html_table(sb_table, fill = TRUE)
derp<-html_table(sb_table)

