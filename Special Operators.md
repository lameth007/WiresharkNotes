# find http request of get and post
http.request.method in {GET,POST}

# find frames with special types
    # Case sensitive
frame contains hack
    # Case insensitive
frame matches hack

# Regular Expressions
 # find frames that contain file extensions php, txt exe


 frame matches "\.(?i)(php|txt|exe|)"

# If case isn't a big deal, you could simplify this to (not sure if this case sensitive or insensitive)

frame matches "\.(php|txt|exe)"