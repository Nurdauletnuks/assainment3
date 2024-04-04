import java.io.FileReader;
import java.io.IOException;
//import java.sql.Connection;
//import java.sql.DRiverManager;
//import java.sql.SQLException;
import java.sql.DatabaseMetaData;
import java.util.Properties;
public class data{
    private static volatile data instance;
    private static final Object lock = new Object();
    private Properties config;
private data(String confF){
    config=new Properties();
    try{
        config.load(new FileReader(confF));
    }catch (IOException a){
        a.printStackTrace();
    }
    //        Initialize database connection
//        String url = "jdbc:mysql://" + config.getProperty("hostname") + "/" + config.getProperty("database");
//        String username = config.getProperty("username");
//        String password = config.getProperty("password");
//        try {
//            connection = DriverManager.getConnection(url, username, password);
//            System.out.println("Database connection established.");
//        } catch (SQLException e) {
//            e.printStackTrace();     }
}
public static data getInstance(String confF){
    if(instance == null){
        synchronized (lock){
            if(instance==null){
                instance=new data(confF);
            }
        }}return instance;

}
public void exQ(String qx){
System.out.println(qx);}
    public Properties getConfig(){
    return config;}
    public static void main(String[] args){
    String configF="C:/Users/ПК/Desktop/config.properties";
    data dbcon= data.getInstance(configF);
    dbcon.exQ("SELECT*From table");
    Properties dfCF = dbcon.getConfig();
    System.out.println("DB connect info"+dfCF);
    }
}


hostname=lokal
username=Nuks
password=ht_jt
database=tab1
