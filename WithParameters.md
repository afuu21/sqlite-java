    /**
     * Get the movies whose actor has apeared more than one time
     * @param count 
     */
    public void getCountGreaterThan(int count){
               String sql = "SELECT movie "
                          + "FROM movies WHERE count(actor) > 1";
        
        try (Connection conn = this.connect();
             PreparedStatement pstmt  = conn.prepareStatement(sql)){
            
            // set the value
            pstmt.setInt(1,count);
            //
            ResultSet rs  = pstmt.executeQuery();
            
            // loop through the result set
            while (rs.next()) {
                System.out.println(rs.getString("movie"));
            }
        } catch (SQLException e) {
            System.out.println(e.getMessage());
        }
    }
![movie-db](https://user-images.githubusercontent.com/55314442/171023989-88d4d168-3675-4211-adfb-bd8ad139ca16.png)
