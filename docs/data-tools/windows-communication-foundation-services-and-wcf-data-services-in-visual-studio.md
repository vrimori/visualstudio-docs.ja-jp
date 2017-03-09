---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 には、分散アプリケーションを作成するための Microsoft のテクノロジである、Windows Communication Foundation \(WCF\) および [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]を扱うためのツールが用意されています。  ここでは、サービスの概要を [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の観点から説明します。  
  
## WCF とは  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] は、セキュリティで保護され、信頼性が高く、トランザクション処理の対象となり、相互運用が可能な分散アプリケーションを作成するための統一されたフレームワークです。  以前のバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、アプリケーション間の通信に使用できる複数のテクノロジがありました。  
  
 どのプラットフォームからでもアクセスできるような仕方で情報を共有したい場合は、Web サービス \(ASMX Web サービスとも呼ばれる\) を使用しました。  クライアントと、Windows オペレーティング システム上で実行されるサーバーとの間で単にデータを移動したい場合は、.NET リモート処理を使用しました。  トランザクション通信を行いたい場合は、Enterprise Services \(DCOM\) を使用し、キュー モデルを使用したい場合はメッセージ キュー \(MSMQ とも呼ばれる\) を使用しました。  
  
 WCF では、これらすべてのテクノロジの機能を、1 つのプログラミング モデルに統一しています。  これにより、分散アプリケーションの開発作業が簡略化されます。  
  
#### WCF データ サービスとは  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]はデータベースと直接対話するサービスで、標準的な HTTP 動詞 \(GET、POST、PUT、DELETE など\) を使用してデータを返すことができます。  一般に、[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]はデータベースでのレコードの作成、更新、または変更に使用されるアプリケーションに適しています。  詳細については、「[ADO.NET Data Services フレームワーク](http://go.microsoft.com/fwlink/?LinkID=119952)」を参照してください。  
  
### WCF のプログラミング モデル  
 WCF プログラミング モデルは、WCF サービスと WCF クライアントとの間の通信に基づいています。  このプログラミング モデルは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の <xref:System.ServiceModel> 名前空間にカプセル化されています。  
  
#### WCF サービス  
 WCF サービスは、サービスとクライアントの間のコントラクトを定義するインターフェイスに基づいています。  次のコードに示すように、<xref:System.ServiceModel.ServiceContractAttribute> 属性で指定されます。  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 WCF サービスによって公開される関数またはメソッドを定義するには、それらに <xref:System.ServiceModel.OperationContractAttribute> 属性を付けます。  また、<xref:System.Runtime.Serialization.DataContractAttribute> 属性で複合型を指定することにより、シリアル化されたデータを公開できます。  これにより、クライアントでデータ バインディングを使用できるようになります。  
  
 インターフェイスとメソッドを定義すると、それらはインターフェイスを実装するクラスにカプセル化されます。  単一の WCF サービス クラスは、複数のサービス コントラクトを実装できます。  
  
 WCF サービスは、*エンドポイント*と呼ばれるものを使用して利用するように公開されます。  エンドポイントは、サービスと通信するための唯一の方法となります。つまり、他のクラスの場合のように直接参照を使用してサービスにアクセスすることはできません。  
  
 エンドポイントは、アドレス、バインディング、コントラクトで構成されます。  アドレスは、サービスのロケーションを定義します。ロケーションは、URL、FTP アドレス、ネットワーク パス、またはローカル パスで指定することができます。  バインディングは、サービスと通信する方法を定義します。  WCF バインディングは、HTTP や FTP といったプロトコル、Windows 認証やユーザー名とパスワードといったセキュリティ機構などを指定するための汎用的なモデルを提供します。  コントラクトには、WCF サービス クラスによって公開される操作が含まれます。  
  
 複数のエンドポイントを単一の WCF サービスに対して公開することができます。  これにより、さまざまなクライアントが同一のサービスとさまざまな方法で通信することができます。  たとえば、銀行のサービスでは、従業員用に 1 つのエンドポイントを用意し、外部の顧客用に別のエンドポイントを用意するかもしれません。それぞれのエンドポイントでは、使用するアドレス、バインディング、コントラクトのいずれか \(あるいはすべて\) が異なります。  
  
#### WCF クライアント  
 WCF クライアントは、アプリケーションが WCF サービスと通信できるようにする*プロキシ*と、サービスに対して定義されているエンドポイントと対応するエンドポイントで構成されます。  プロキシは、クライアント側の app.config ファイルで生成されます。プロキシには、サービスによって公開される型とメソッドに関する情報が含まれます。  複数のエンドポイントを公開するサービスの場合は、クライアントがその必要に合った最適なものを選択することができます。たとえば、HTTP 経由で通信し Windows 認証を使用するというような必要に合わせて選択できます。  
  
 WCF クライアントの作成後は、他のオブジェクトの場合と同じように、コード内でサービスを参照します。  たとえば、前の例で示した `GetData` メソッドを呼び出すには、次のようなコードを記述できます。  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Visual Studio の WCF ツール  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 には、WCF サービスと WCF クライアントの両方を作成するのに役立つツールが用意されています。  ツールを紹介するチュートリアルについては、「[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)」を参照してください。  
  
### WCF サービスの作成とテスト  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テンプレートを基にして、独自のサービスを短時間で作成できます。  その後、WCF Service Auto Host と WCF Test Client を使用してサービスをデバッグおよびテストできます。  これらのツールにより、迅速で簡単なデバッグおよびテスト サイクルが実現し、早い段階でホスト モデルにコミットする必要がなくなります。  
  
#### WCF テンプレート  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テンプレートには、サービス開発のための基本的なクラス構造が用意されています。  いくつかの WCF テンプレートが **\[新しいプロジェクトの追加\]** ダイアログ ボックスで選択できます。  使用できるテンプレートには、WCF Service Library プロジェクト、WCF Service Web Sites、および WCF Service Item テンプレートがあります。  
  
 テンプレートを選択すると、サービス コントラクト、サービス実装、サービス構成用にファイルが追加されます。  必要な属性は既に追加されており、コードを一切記述しなくても、単純な "Hello World" タイプのサービスが作成されます。  実際のサービス用には、関数とメソッドを提供するコードを追加する必要がありますが、テンプレートによって基本的な基盤が提供されます。  
  
 WCF テンプレートの詳細については、「[WCF Visual Studio テンプレート](../Topic/WCF%20Visual%20Studio%20Templates.md)」を参照してください。  
  
#### WCF Service Host  
 WCF サービス プロジェクトに対して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーを開始すると \(F5 を押す\)、WCF Service Host ツールがローカルでのサービスのホストを自動的に開始します。  WCF Service Host は、WCF サービス プロジェクト内のサービスを列挙し、プロジェクトの構成をロードし、検出された各サービスに対するホストをインスタンス化します。  
  
 WCF Service Host を使用することにより、開発中に追加のコードを記述したり、特定のホストにコミットしたりすることなく、WCF サービスをテストできます。  
  
 WCF Service Host の詳細については、「[WCF サービス ホスト \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md)」を参照してください。  
  
#### WCF テスト クライアント  
 WCF Test Client ツールによって、テスト パラメーターを入力し、その入力を WCF サービスに送信し、サービスが送り返す応答を表示することができます。  WCF Service Host と組み合わせて使用すると、サービスのテスト作業が簡単になります。  
  
 F5 を押して WCF サービス プロジェクトをデバッグすると、WCF Test Client が開き、構成ファイルで定義されているサービス エンドポイントの一覧が表示されます。  パラメーターをテストしてサービスを開始し、このプロセスを繰り返すことによって、サービスのテストと検証を継続的に行えます。  
  
 WCF Test Client の詳細については、「[WCF のテスト用クライアント \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md)」を参照してください。  
  
### Visual Studio での WCF サービスへのアクセス  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はWCF クライアントを作成するタスクを簡略化し自動的に\[ENT0ENT\] ダイアログ ボックスを使用して追加するサービスのプロキシとエンドポイントを生成します。  必要な構成情報はすべて app.config ファイルに追加されます。ほとんどの場合、必要な作業は、サービスを使用するためにインスタンス化することだけです。  
  
 **\[サービス参照の追加\]** ダイアログ ボックスでは、サービスのアドレスを入力するか、ソリューション内で定義されているサービスを検索することができます。  このダイアログ ボックスでは、サービスの一覧と、それらのサービスによって提供される操作の一覧が表示されます。  また、コード内でサービスを参照する際に使用する名前空間を定義することもできます。  
  
 **\[サービス参照の構成\]** ダイアログ ボックスでは、サービスの構成をカスタマイズできます。  サービスのアドレスの変更や、アクセス レベル、非同期動作、メッセージ コントラクト タイプの指定、型の再利用の構成を行うことができます。  
  
## 方法 : サービス エンドポイントを選択します。  
 WCF \(Windows Communication Foundation\) サービスの中には、クライアントがサービスとの通信に使用できるエンドポイントを複数公開するものがあります。  たとえば、第 1 のエンドポイントでは HTTP バインディングおよびユーザー名とパスワードのセキュリティを使用し、第 2 のエンドポイントでは FTP および Windows 認証を使用するような場合です。  第 1 のエンドポイントはファイアウォールの外側からサービスにアクセスするアプリケーションが使用し、第 2 のエンドポイントはイントラネットで使用されます。  
  
 このような場合は、サービス参照のコンストラクターに対するパラメーターとして `endpointConfigurationName` を指定できます。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### サービスのエンドポイントを選択するには  
  
1.  WCF サービスへの参照を追加します。  詳細については、「[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)」を参照してください。  
  
2.  コード エディターで、サービス参照のコンストラクターを追加します。  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  *ServiceReference* をサービス参照の名前空間に置き換え、*Service1Client* をサービスの名前に置き換えます。  
  
3.  IntelliSense リストに、コンストラクターのオーバーロードが表示されます。  `endpointConfigurationName As String` オーバーロードを選択します。  
  
4.  オーバーロードの後に「`=` *ConfigurationName*」と入力します。*ConfigurationName* は、使用するエンドポイントの名前です。  
  
    > [!NOTE]
    >  使用できるエンドポイントの名前がわからない場合は、app.config ファイルで検索できます。  
  
#### WCF サービスで使用できるエンドポイントを検索するには  
  
1.  **ソリューション エクスプローラー**で、サービス参照を含むプロジェクトの app.config ファイルを右クリックし、**\[開く\]** をクリックします。  ファイルがコード エディターに表示されます。  
  
2.  ファイルで `<Client>` タグを探します。  
  
3.  `<Client>` タグの下で、`<Endpoint>` で始まるタグを探します。  
  
     サービス参照が複数のエンドポイントを提供している場合は、複数の `<Endpoint` タグがあります。  
  
4.  `<EndPoint>` タグの内部には、`name="`*SomeService*`"` パラメーターがあります \(*SomeService* はエンドポイント名を表します\)。  これが、サービス参照のコンストラクターの `endpointConfigurationName As String` オーバーロードに渡すことのできるエンドポイントの名前です。  
  
## 方法 : サービスのメソッドを非同期的に呼び出します  
 WCF \(Windows Communication Foundation\) のほとんどのメソッドは、同期的にも非同期でも呼び出すことができます。  メソッドを非同期で呼び出すと、アプリケーションが低速接続で実行しているときでも、メソッドの呼び出し中にアプリケーションの動作を継続できます。  
  
 既定では、プロジェクトにサービス参照を追加すると、メソッドを同期的に呼び出すようにプロジェクトが構成されます。  **\[サービス参照の構成\]** ダイアログ ボックスで設定を変更することによって、メソッドを非同期で呼び出すように動作を変更できます。  
  
> [!NOTE]
>  このオプションはサービスごとに設定されます。  サービスのメソッドの 1 つを非同期で呼び出す場合は、すべてのメソッドを非同期で呼び出す必要があります。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### サービス メソッドを非同期で呼び出すには  
  
1.  **ソリューション エクスプローラー**で、サービス参照を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[サービス参照の構成\]** をクリックします。  
  
3.  **\[サービス参照の構成\]** ダイアログ ボックスで、**\[非同期操作の生成\]** チェック ボックスをオンにします。  
  
## 方法 : サービスから返されたデータをバインドできます。  
 WCF \(Windows Communication Foundation\) サービスから返されたデータは、他のデータ ソースと同様に、コントロールにバインドできます。  WCF サービスへの参照を追加すると、データを返す複合型がサービスに含まれる場合、これらの型は **\[データ ソース\]** ウィンドウに自動的に追加されます。  
  
#### WCF サービスによって返された 1 つのデータ フィールドにコントロールをバインドするには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  **\[データ ソース\]** ウィンドウが表示されます。  
  
2.  **\[データ ソース\]** ウィンドウで、サービス参照についてのノードを展開します。  サービスから返される複合型があれば、すべて表示されます。  
  
3.  型についてのノードを展開します。  その型についてのデータ フィールドが表示されます。  
  
4.  フィールドを選択してドロップダウン矢印をクリックすると、このデータ型に使用できるコントロールの一覧が表示されます。  
  
5.  バインド先となるコントロールの型をクリックします。  
  
6.  フィールドをフォームにドラッグします。  コントロールが、<xref:System.Windows.Forms.BindingSource> コンポーネントおよび <xref:System.Windows.Forms.BindingNavigator> コンポーネントと共にフォームに追加されます。  
  
7.  バインドする他のフィールドに対して、手順 4. ～ 6. を繰り返します。  
  
#### WCF サービスから返される複合型にコントロールをバインドするには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  **\[データ ソース\]** ウィンドウが表示されます。  
  
2.  **\[データ ソース\]** ウィンドウで、サービス参照についてのノードを展開します。  サービスから返される複合型があれば、すべて表示されます。  
  
3.  型についてのノードを選択してドロップダウン矢印をクリックすると、使用できるオプションの一覧が表示されます。  
  
4.  **DataGridView** をクリックしてデータをグリッドで表示するか、**\[詳細\]** をクリックして個々のコントロールにデータを表示します。  
  
5.  ノードをフォームにドラッグします。  コントロールが、<xref:System.Windows.Forms.BindingSource> コンポーネントおよび <xref:System.Windows.Forms.BindingNavigator> コンポーネントと共にフォームに追加されます。  
  
## 方法 : サービスを既存の型を再利用するように構成します。  
 プロジェクトにサービス参照を追加すると、そのサービスで定義されている型がすべてローカル プロジェクトで生成されます。  この結果、共通の [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の型がサービスで使用されていたり、型が共有ライブラリに定義されていたりすると、重複する型が作成されることがよくあります。  
  
 この問題を回避するために、参照されるアセンブリの型は既定で共有されます。  1 つ以上のアセンブリで型の共有を無効にするには、**\[サービス参照の構成\]** ダイアログ ボックスを使用します。  
  
#### 1 つのアセンブリで型の共有を無効にするには  
  
1.  **ソリューション エクスプローラー**で、サービス参照を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[サービス参照の構成\]** をクリックします。  
  
3.  **\[サービス参照の構成\]** ダイアログ ボックスで、**\[参照されたアセンブリを指定して型を再利用\]** をオンにします。  
  
4.  型の共有を有効にするアセンブリごとに、チェック ボックスをオンにします。  アセンブリで型の共有を無効にするには、チェック ボックスをオフのままにします。  
  
#### すべてのアセンブリで型の共有を無効にするには  
  
1.  **ソリューション エクスプローラー**で、サービス参照を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[サービス参照の構成\]** をクリックします。  
  
3.  **\[サービス参照の構成\]** ダイアログ ボックスで、**\[参照されたアセンブリで型を再利用\]** チェック ボックスをオフにします。  
  
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での WCF サービスの作成と使用について順を追って説明します。|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] における [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]の作成と使用の手順を説明します。|  
|[WCF 開発ツールの使用](../Topic/Using%20the%20WCF%20Development%20Tools.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で WCF サービスを作成してテストする方法について説明します。|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|プロジェクトに対して WCF サービスの追加、更新、および削除を行う方法について説明します。|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]を参照して使用する方法について説明します。|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|XML \(ASMX\) Web サービスへの参照をプロジェクトに追加する方法について説明します。|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|サービス参照で発生することの多いエラーと、その回避方法を示します。|  
|[WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)|WCF サービスのデバッグ時に発生する一般的な問題、およびデバッグの手法について説明します。|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|WCF を使用して Web サイトのロール サービスを提供する方法について説明します。|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/ja-jp/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|.NET Compact Framework の WCF メッセージング層のサポートについて説明します。|  
|[チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|型指定されたデータセットを作成し、TableAdapter とデータセット コードを複数のプロジェクトに分離する方法の詳細な手順について説明します。|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|**\[サービス参照の追加\]** ダイアログ ボックスのユーザー インターフェイス要素を説明します。|  
|[\[サービス参照の構成\] ダイアログ ボックス](../Topic/Configure%20Service%20Reference%20Dialog%20Box.md)|**\[サービス参照の構成\]** ダイアログ ボックスのユーザー インターフェイス要素を説明します。|  
  
## Reference  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>