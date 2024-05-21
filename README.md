# SCADA-system-
Creating SCADA system for heating system for differnent outer stations 
********************************************************************************************************
Testing 
********************************************************************************************************
Testing reading data from Matrikon OPC DA server simulator 
<img width="771" alt="Test opc da and visual studio" src="https://github.com/OlaReda1/SCADA-system-/assets/112081320/4c0149eb-43c1-4f61-9539-b55397a073d0">





********************************************************************************************************
Testing logging data to SQL mangement serve

Install-Package System.Data.SqlClient

----------------------------------------
Code
----------------------------------------
 public void LogToSQLDatabase()

 {
     string Area = "Engervann";
     DateTime time = DateTime.Now;
     double TemperatureValue = 10;
     string connectionString = "Server=DESKTOP-UK29356\\SQLEXPRESS;Database=StationsTemp;User Id=sa;Password=Zayd2023;";
     // Create a SqlConnection
     SqlConnection connection = new SqlConnection(connectionString);
     string query = "INSERT INTO StationsTemp (Area, time, TemperatureValue) VALUES (@Area, @time, @TemperatureValue)";
     try
     {
         // Open the connection
         connection.Open();

         // Create a SqlCommand
         SqlCommand command = new SqlCommand(query, connection);

         // Define parameters and their values
         command.Parameters.AddWithValue("@Area", Area);
         command.Parameters.AddWithValue("@time", time);
         command.Parameters.AddWithValue("@TemperatureValue", TemperatureValue);

         // Execute the command
         int rowsAffected = command.ExecuteNonQuery();

         textBox1.Text = "Done logging ";

     }
     catch (Exception ex)
     {
         // Handle exceptions
         MessageBox.Show(ex.Message);
     }

 }
    private void LoggBT_Click(object sender, EventArgs e)
    {
        LogToSQLDatabase();
    }
}



***********************************************************************************************************************************
Recive data from Labview by using 
Install-Package OpcLabs.QuickOpc



