---
title: "チュートリアル: ADO.NET を使用した単純なデータ アプリケーションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 42
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: ADO.NET を使用した単純なデータ アプリケーションの作成
データベースのデータを処理するアプリケーションの作成では、接続文字列の定義、データの挿入、ストアド プロシージャの実行などの基本的なタスクを実行します。  このトピックでは、Visual C\#、Visual Basic および ADO.NET 使用した簡単な Windows フォーム アプリケーション内部から、データベースとやり取りする方法を説明します。  
  
> [!IMPORTANT]
>  コードをシンプルにするため、運用環境で使用する例外処理は含まれていません。  
  
 **このトピックの内容**  
  
-   [サンプル データベースを設定する](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [フォームを作成してコントロールを追加する](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [接続文字列を保存する](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [接続文字列を取得する](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [フォームのコードを記述する](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [アプリケーションをテストする](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## 必須コンポーネント  
 アプリケーションの作成には、次が必要です:  
  
-   Visual Studio 2012 と更新プログラム 1 または [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]  
  
-   SQL Server 2012 Express LocalDB  
  
-   「[チュートリアル: サイズの小さいサンプル データベースの作成](../data-tools/create-a-sql-database-by-using-a-script.md)」の手順に従って作成する、小さいサンプル データベース。  
  
-   設定が完了したデータベースへの接続文字列。  **SQL Server オブジェクト エクスプローラー**を開き、データベースのショートカット メニューを開き、**\[プロパティ\]** をクリックし、**\[接続文字列\]** プロパティにスクロールします。  
  
 このトピックは、Visual Studio IDE の基本的な機能を理解していて、Windows フォーム アプリケーションの作成、そのプロジェクトへのフォームの追加、フォームにボタンなどのコントロールの追加、コントロールのプロパティの設定、およびシンプルなイベントのコード記述ができることを前提としています。  これらのタスクに慣れていない場合、「[Visual C\# と Visual Basic の概要](../ide/getting-started-with-visual-csharp-and-visual-basic.md)」を完了してからこのトピックを開始することをお勧めします。  
  
##  <a name="BKMK_setupthesampledatabase"></a> サンプル データベースを設定する  
 このチュートリアルで扱うサンプル データベースには、「Customer \(顧客\)」と「Order \(注文\)」のテーブルがあります。  最初はテーブルにデータはありませんが、作成したアプリケーションを実行するとデータが追加されます。  データベースには、5 種類のシンプルなストアド プロシージャもあります。  「[チュートリアル: サイズの小さいサンプル データベースの作成](../data-tools/create-a-sql-database-by-using-a-script.md)」には、テーブル、主キーおよび外部キー、制約、ストアド プロシージャなどを作成する Transact\-SQL スクリプトが含まれています。  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> フォームを作成してコントロールを追加する  
  
1.  Windows フォーム アプリケーションのプロジェクトを作成し、`SimpleDataApp` という名前を付けます。  
  
     Visual Studio は、Form1 という名前の空の Windows フォームを含めた、いくつかのファイルとプロジェクトを作成します。  
  
2.  2 つの Windows フォームをプロジェクトに追加し、合計 3 つのフォームに次の名前を付けます。  
  
    -   ナビゲーション  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  各フォームに、次の図に示されるように、テキスト ボックス、ボタン、および他のコントロールを追加します。  各コントロールに、テーブルを示すプロパティを設定します。  
  
    > [!NOTE]
    >  グループ ボックス、およびラベル コントロールは明確性を追加しますが、コードでは使用されません。  
  
 **Navigation フォーム**  
  
 ![ナビゲーション ダイアログ ボックス](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Navigation フォームのコントロール|プロパティ|  
|----------------------------|-----------|  
|ボタン|Name \= btnGoToAdd|  
|ボタン|Name \= btnGoToFillOrCancel|  
|ボタン|Name \= btnExit|  
  
 **NewCustomer フォーム**  
  
 ![新しい顧客を追加して注文を作成する](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|NewCustomer フォームのコントロール|プロパティ|  
|-----------------------------|-----------|  
|TextBox|Name \= txtCustomerName|  
|TextBox|Name \= txtCustomerID<br /><br /> Readonly \= True|  
|ボタン|Name \= btnCreateAccount|  
|NumericUpdown|DecimalPlaces \= 0<br /><br /> Maximum \= 5000<br /><br /> Name \= numOrderAmount|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpOrderDate|  
|ボタン|Name \= btnPlaceOrder|  
|ボタン|Name \= btnAddAnotherAccount|  
|ボタン|Name \= btnAddFinish|  
  
 **FillOrCancel フォーム**  
  
 ![注文の入力または取り消し](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|FillOrCancel フォームのコントロール|プロパティ|  
|------------------------------|-----------|  
|TextBox|Name \= txtOrderID|  
|ボタン|Name \= btnFindByOrderID|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpFillDate|  
|DataGridView|Name \= dgvCustomerOrders<br /><br /> Readonly \= True<br /><br /> RowHeadersVisible \= False|  
|ボタン|Name \= btnCancelOrder|  
|ボタン|Name \= btnFillOrder|  
|ボタン|Name \= btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> 接続文字列を保存する  
 アプリケーションがデータベースの接続を開くとき、アプリケーションは接続文字列にアクセスする必要があります。  各フォームで文字列を手動で入力することを回避するため、プロジェクトのアプリケーション構成ファイルに文字列を保存し、アプリケーションから呼び出された場合にいつでもこの文字列を戻す、メソッドを作成します。  
  
1.  プロジェクトのショートカット メニューを開き、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウの左パネルで、**\[設定\]** をクリックします。  
  
3.  **名前**の列に、「`connString`」と入力します。  
  
4.  **\[種類\]** ボックスの一覧にある **\(接続文字列\)** を選択します。  
  
5.  **\[スコープ\]** ボックスの一覧にある、**アプリケーション**を選択します。  
  
6.  **\[値\]** の列に接続文字列を入力し、変更内容を保存します。  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> 接続文字列を取得する  
  
1.  メニュー バーで、**\[プロジェクト\]**、**\[参照の追加\]** の順にクリックし、System.Configuration.dll に参照を追加します。  
  
2.  メニュー バーで、**\[プロジェクト\]**、**\[クラスの追加\]** の順に選択し、プロジェクトにクラス ファイルを追加してそのファイル名を `Utility` とします。  
  
     Visual Studio はファイルを作成し、それを **\[ソリューション エクスプローラー\]** に表示します。  
  
3.  Utility ファイルでプレースホルダー コードを次のコードに置き換えます。  コードのセクションを識別する \(Util\- が付けられた\) 番号付きのコメントを確認します。  テーブルはコードに従ってキー ポイントを呼び出します。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |コメント|説明|  
    |----------|--------|  
    |Util\-1|System.Configuration 名前空間を追加します。|  
    |Util\-2|変数 `returnValue` を定義し、`null` \(C\#\)、または `Nothing` \(Visual Basic\) に初期化します。|  
    |Util\-3|`[プロパティ]` のウィンドウで接続文字列名を「**connString**」と入力した場合でも、コードに `"SimpleDataApp.Properties.Settings.connString"` \(C\#\)、または `"SimpleDataApp.My.MySettings.connString"` \(Visual Basic\) を指定する必要があります。|  
  
##  <a name="BKMK_writethecodefortheforms"></a> フォームのコードを記述する  
 このセクションには、各フォームの動作を簡単な概要と、フォームを作成するコードがあります。  番号付きコメントは、コードのセクションを識別します。  
  
### Navigation フォーム  
 Navigation フォームはアプリケーションを実行すると開きます。  **\[Add an account\]** は NewCustomer フォームを開きます。  **\[Fill or cancel orders\]** は FillOrCancel フォームを開きます。  **\[終了\]** は、アプリケーションを閉じます。  
  
#### Navigation フォームをスタートアップ フォームに設定  
 C\# を使用している場合、**\[ソリューション エクスプローラー\]** で Program.cs を開き、`Application.Run` の行を次のように変更します: `Application.Run(new Navigation());`  
  
 Visual Basic を使用している場合、**\[ソリューション エクスプローラー\]** で、**\[プロパティ\]** ウィンドウを開き、**\[アプリケーション\]** をクリックして、**\[スタートアップ フォーム\]** の一覧から SimpleDataApp.Navigation を選択します。  
  
#### イベント ハンドラーを作成する  
 フォームのボタン 3 つに空のクリック イベント ハンドラーを作成します。  「[方法 : Windows フォーム デザイナーで既定のイベント ハンドラーを作成する](http://msdn.microsoft.com/ja-jp/757bcc16-1dc2-4d68-b115-ac0f53f05c8d)」を参照してください。  
  
#### Navigation のコードを作成する  
 Navigation フォームで、既存のコードを次のコードに書き換えます。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### NewCustomer フォーム  
 顧客名を入力し **\[Create Account\]** をクリックすると、NewCustomer フォームは、顧客アカウントを作成し、SQL Server は新しいアカウント番号として IDENTITY 値を戻します。  数量と注文日を指定してこの新しいアカウントの注文を設定し、**\[Place Order\]** をクリックします。  
  
#### イベント ハンドラーを作成する  
 フォームの各ボタン空のクリック イベント ハンドラーを作成します。  
  
#### NewCustomer のコードを作成する  
 NewCustomer フォームに次のコードを追加します。  番号付きコメントおよびコードに続くテーブルを使用して、各コード ブロックをステップ実行します。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open)  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is the orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try – catch - finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 add return value for stored procedure, which is the orderID  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try – catch - finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could not not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|コメント|説明|  
|----------|--------|  
|NC\-1|名前空間の一覧に System.Data.SqlClient および System.Configuration を追加します。|  
|NC\-2|後で使用する `parsedCustomerID` および `orderID` の変数を宣言します。|  
|NC\-3|アプリケーション構成ファイルから接続文字列を取得するための `GetConnectionString` のメソッドを呼び出し、`connstr` 文字列変数を格納します。|  
|NC\-4|`btnCreateAccount` ボタンのクリック イベント ハンドラーのコードを追加します。|  
|NC\-5|`isCustomerName` が顧客名の存在する場合にのみ実行されるように、クリック イベント コードの `uspNewCustomer` への呼び出しをラップします。|  
|NC\-6|`SqlConnection` オブジェクト \(`conn`\) を作成し、`connstr` 接続文字列に渡します。|  
|NC\-7|`SqlCommand` オブジェクト `cmdNewCustomer` を作成します。<br /><br /> -   ストアド プロシージャとして実行する `Sales.uspNewCustomer` を指定します。<br />-   コマンドがストアド プロシージャであることを指定する `CommandType` プロパティを使用します。|  
|NC\-8|ストアド プロシージャからの `@CustomerName` 入力パラメーターを追加します。<br /><br /> -   `Parameters` コレクションにパラメーターを追加します。<br />-   SqlDbType 列挙を使用して、パラメーターの型を nvarchar\(40\) と指定します。<br />-   `txtCustomerName.Text` をソースとして指定します。|  
|NC\-9|ストアド プロシージャからの出力パラメーターを追加します。<br /><br /> -   `Parameters` コレクションにパラメーターを追加します。<br />-   `ParameterDirection.Output` を使用して、パラメーターを出力として識別します。|  
|NC\-10|接続を開くための Try \- Catch \- Finally のブロックを追加してストアド プロシージャを実行し、例外を処理した後に接続を閉じます。|  
|NC\-11|NC\-6 で作成した接続 \(`conn`\) を開きます。|  
|NC\-12|`cmdNewCustomer` の `ExecuteNonQuery` メソッドを使用して、クエリではなく `Sales.uspNewCustomer` ステートメントを実行する `INSERT` ストアド プロシージャを実行します。|  
|NC\-13|データベースから IDENTITY 値として `@CustomerID` の値が戻されます。  これは整数であるため、\[Customer ID\] ボックスに表示するために文字列に変換する必要があります。<br /><br /> -   NC\-2 で `parsedCustomerID` を宣言しています。<br />-   後で使用するため、`@CustomerID` に `parsedCustomerID` 値を格納します。<br />-   戻された Customer ID \(顧客 ID\) を文字列に変換し、`txtCustomerID.Text` に挿入します。|  
|NC\-14|このサンプルでは、シンプルな、製品レベルの品質ではない catch 句を追加します。|  
|NC\-15|使用の終了後必ず接続を閉じ、接続プールに解放できるようします。  「[SQL Server Connection Pooling \(ADO.NET\) \(SQL Server の接続プール \(ADO.NET\)\)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx)」を参照してください。|  
|NC\-16|顧客名が存在することを確認するメソッドを定義します。<br /><br /> -   アカウントの作成にいは名前が必要であるため、テキスト ボックスが空の場合はメッセージを表示して `false` を返します。<br />-   テキスト ボックスが空ではない場合、`true` を返します。|  
|NC\-17|`btnPlaceOrder` ボタンのクリック イベント ハンドラーのコードを追加します。|  
|NC\-18|必要な入力が存在しない場合に `isPlaceOrderReady` を実行しないように、`btnPlaceOrder_Click` イベント コードの `uspPlaceNewOrder` への呼び出しをラップします。|  
|NC\-19 から NC\-25|これらのセクションのコードは、`btnCreateAccount_Click` イベント ハンドラーに追加したコードと類似しています。<br /><br /> -   NC\-19。  `SqlCommand` オブジェクトの `cmdNewOrder` を作成し、ストアド プロシージャとして `Sales.uspPlaceOrder` を指定します。<br />-   NC\-20 から NC\-23 は、ストアド プロシージャの入力パラメーターです。<br />-   NC\-24.  `@RC` はデータベースから生成された注文 ID の戻り値を含みます。  このパラメーターの方向は `ReturnValue` として指定されます。<br />-   NC\-25.  Order ID \(注文 ID\) の値を NC\-2 で宣言した `orderID` 変数に格納し、メッセージ ボックスに値を表示します。|  
|NC\-26|Customer ID \(顧客 ID\) が存在すること、および `numOrderAmount` で Amount \(数量\) が指定されていることを確認するメソッドを定義します。|  
|NC\-27|`ClearForm` イベント ハンドラーの `btnAddAnotherAccount` メソッドを呼び出します。|  
|NC\-28|別の顧客を追加するために、フォームから値をクリアする `ClearForm` メソッドを作成します。|  
|NC29|NewCustomer フォームを閉じて、Navigation フォームにフォーカスを戻します。|  
  
### FillOrCancel フォーム  
 FillorCancel フォームは、Order ID \(注文 ID\) を入力して **\[Find Order\]** のボタンを選択したときに、Order \(注文\) を戻すクエリを実行します。  戻された行は読み取り専用なデータ グリッドに表示されます。  **\[Cancel Order\]** をクリックして、注文をキャンセル \(X\) としてマークできます。また **\[Fill Order\]** をクリックして、注文を満たした \(F\) としてマークできます。  **\[Find Order\]** をもう一度クリックすると、更新された行が表示されます。  
  
#### イベント ハンドラーを作成する  
 フォームのボタン 4 つに空のクリック イベント ハンドラーを作成します。  
  
#### FillOrCancel のコードを作成する  
 FillOrCancel フォームに次のコードを追加します。  番号付きコメントおよびコードに続くテーブルを使用して、コード ブロックをステップ実行します。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try – catch - finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the datatable in the datagridview.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try – catch - finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from the SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the datagridview.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|コメント|説明|  
|----------|--------|  
|FC\-1|名前空間の一覧に System.Data.SqlClient、System.Configuration および System.Text.RegularExpressions を追加します。|  
|FC\-2|変数 `parsedOrderID` を宣言します。|  
|FC\-3|アプリケーション構成ファイルから接続文字列を取得するための `GetConnectionString` のメソッドを呼び出し、`connstr` 文字列変数を格納します。|  
|FC\-4|`btnFindOrderByID` のクリック イベント ハンドラーのコードを追加します。|  
|FC\-5|慣れてきましたか?  これらのタスクは SQL ステートメントまたはストアド プロシージャを実行する前に必要です。<br /><br /> -   SqlConnection オブジェクトを作成します。<br />-   SQL ステートメントを定義、またはストアド プロシージャの名前を指定します。  \(ここでは、`SELECT` ステートメントを実行します。\)<br />-   `SqlCommand` オブジェクトを作成します。<br />-   SQL ステートメントまたはストアド プロシージャのパラメーターを定義します。|  
|FC\-6|このコードは、クエリの結果を取得して表示するために `SqlDataReader` および `DataTable` を使用します。<br /><br /> -   接続を開きます。<br />-   `rdr` の `cmdOrderID` メソッドを実行して、SqlDataReader の `ExecuteReader` を作成します。<br />-   取得したデータを保持するため `DataTable` オブジェクトを作成します。<br />-   `SqlDataReader` オブジェクトに `DataTable` からデータを読み込みます。<br />-   `DataTable` を datagridview の `DataSource` として指定することによって、datagridview にデータを表示します。<br />-   SqlDataReader を閉じます。|  
|FC\-7|`btnCancelOrder` のクリック イベント ハンドラーのコードを追加します。  このコードは `Sales.uspCancelOrder` ストアド プロシージャを実行します。|  
|FC\-8|`btnFillOrder` のクリック イベント ハンドラーのコードを追加します。  このコードは `Sales.uspFillOrder` ストアド プロシージャを実行します。|  
|FC\-9|`OrderID` が `SqlCommand` オブジェクトへのパラメーターとして送信する準備が完了していることを、確認するメソッドを作成します。<br /><br /> -   ID が `txtOrderID` に入力されていることを確認します。<br />-   整数以外の文字をシンプルにチェックする定義に `Regex.IsMatch` を使用します。<br />-   FC\-2 で `parsedOrderID` の変数を宣言しています。<br />-   入力が有効な場合は、テキストを整数に変換し、`parsedOrderID` 変数に値を格納します。<br />-   `isOrderID`、`btnFindByOrderID` および `btnCancelOrder` のクリック イベント ハンドラーの周囲に `btnFillOrder` のメソッドをラップします。|  
  
##  <a name="BKMK_testyourapplication"></a> アプリケーションをテストする  
 各クリック イベント ハンドラーをコードし、コードの記述を完了した後、F5 キーを選択してアプリケーションのビルドとテストを実行します。