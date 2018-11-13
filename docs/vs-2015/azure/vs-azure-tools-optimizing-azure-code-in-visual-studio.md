---
title: Visual Studio での Azure コードの最適化 |Microsoft Docs
description: によって、コードの堅牢性とパフォーマンスを向上が Visual Studio での最適化ツール Azure コードに関するヘルプについて説明します。
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002519"
---
# <a name="optimizing-your-azure-code"></a>Azure のコードの最適化
Microsoft Azure を使用するアプリをプログラミングしている場合は、コーディング プラクティス、アプリケーションのスケーラビリティ、動作、およびクラウド環境でのパフォーマンスに関する問題を回避するために従う必要があります。 Microsoft を認識し、これら一般的に発生する問題のいくつかとその解決に役立つ Azure コード分析ツールを提供します。 NuGet を使用して Visual Studio でツールをダウンロードすることができます。

## <a name="azure-code-analysis-rules"></a>Azure コード分析規則
Azure コード分析ツールでは、次の規則を使用して、パフォーマンスに影響を与える既知の問題を見つけたときに、Azure のコードを自動的にフラグします。 問題は、警告として表示されます。 検出されたか、コンパイラ エラー。 コード修正や提案、警告またはエラーを解決するのには、多くの場合、電球アイコンが提供されます。

## <a name="avoid-using-default-in-process-session-state-mode"></a>既定 (インプロセス) のセッション状態モードを使用しないでください。
### <a name="id"></a>ID
AP0000

### <a name="description"></a>説明
クラウド アプリケーションの既定 (インプロセス) のセッション状態モードを使用する場合、セッション状態が失われることができます。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
既定では、web.config ファイルで指定されたセッション状態モードは、プロセスでは。 また、エントリがない場合、構成ファイルで指定された、プロセス内にセッション状態モードが既定値です。 インプロセス モードでは、web サーバー上のメモリの中にセッション状態が格納されます。 インスタンスが再起動または負荷分散またはフェールオーバーのサポートの新しいインスタンスが使用される、web サーバーのメモリに格納されているセッション状態は保存されません。 このような状況では、クラウドでスケーラブルなアプリケーションができないようにします。

ASP.NET セッション状態は、セッション状態データのいくつかの別のストレージ オプションをサポートしています: InProc、StateServer、SQLServer、Custom、Off となります。 など、外部のセッション状態ストアのデータをホストするカスタム モードを使用することをお勧め[Redis の Azure セッション状態プロバイダー](http://go.microsoft.com/fwlink/?LinkId=401521)します。

### <a name="solution"></a>ソリューション
1 つの推奨されるソリューションでは、マネージ キャッシュ サービス セッション状態を格納します。 使用する方法について説明します[Redis の Azure セッション状態プロバイダー](http://go.microsoft.com/fwlink/?LinkId=401521)セッション状態を保存します。 クラウド上で、アプリケーションはスケーラブルなことを確認するには、他の場所にセッション状態を格納することもできます。 詳細については、代替のソリューションをお読みくださいは[セッション状態モード](https://msdn.microsoft.com/library/ms178586)します。

## <a name="run-method-should-not-be-async"></a>Run メソッドを非同期にしません。
### <a name="id"></a>ID
AP 1000

### <a name="description"></a>説明
非同期メソッドの作成 (など[await](https://msdn.microsoft.com/library/hh156528.aspx)) の外部、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッドから非同期メソッドを呼び出して、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)します。 宣言、 [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッドを非同期とワーカー ロールの再起動ループに入ります。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
内で非同期メソッドを呼び出す、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッドにより、クラウド サービスのランタイム worker ロールを再利用します。 Worker ロールの開始時にすべてのプログラム実行内で行われて、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッド。 終了、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッドにより、ワーカー ロールが再起動します。 Worker ロールのランタイムが非同期メソッドに達するときに、非同期メソッドの後にすべての操作をディスパッチし、返します。 これが原因で終了する worker ロール、 [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッドを再起動します。 実行の次のイテレーションでワーカー ロール非同期メソッドをもう一度ヒットしても再度をリサイクルする、worker ロールの再起動します。

### <a name="solution"></a>ソリューション
以外のすべての非同期操作を配置、 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)メソッド。 内からは、リファクタリングされた非同期メソッドを呼び出して、 [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) RunAsync () .wait などのメソッド。 Azure コード分析ツールは、この問題を解決するのに役立ちます。

次のコード スニペットでは、この問題に対してコード修正を示しています。

```
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus 共有アクセス署名認証の使用
### <a name="id"></a>ID
AP2000

### <a name="description"></a>説明
認証に Shared Access Signature (SAS) を使用します。 Service bus の認証に access Control Service (ACS) は非推奨です。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
セキュリティ強化のため Azure Active Directory は ACS 認証に代わって SAS 認証します。 参照してください[Azure Active Directory は ACS の未来](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/)については、移行計画します。

### <a name="solution"></a>ソリューション
アプリで SAS 認証を使用します。 次の例では、service bus 名前空間またはエンティティにアクセスする既存の SAS トークンを使用する方法を示します。

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

詳細については、次のトピックを参照してください。

* 概要については、次を参照してください[Service Bus による Shared Access Signature 認証。](https://msdn.microsoft.com/library/dn170477.aspx)
* [Service Bus による Shared Access Signature 認証を使用する方法](https://msdn.microsoft.com/library/dn205161.aspx)
* サンプル プロジェクトでは、次を参照してください[Service Bus サブスクリプションで使用する Shared Access Signature (SAS) 認証。](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>「受信ループ」を回避するために OnMessage メソッドの使用を検討します。
### <a name="id"></a>ID
AP2002

### <a name="description"></a>説明
「受信ループ」に入らないようにする呼び出し、 **OnMessage**メソッドが呼び出すよりもメッセージを受信するためのより優れたソリューション、**受信**メソッド。 ただし、使用する場合、**受信**既定以外のサーバー待機時間を指定して、メソッド、サーバー待機時間が 1 つ分を超えるかどうかを確認してください。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
呼び出すときに**OnMessage**クライアントは、キューまたはサブスクリプションを常にポーリングする内部メッセージ ポンプを起動します。 このメッセージ ポンプにメッセージを受信する呼び出しを発行する無限ループが含まれています。 呼び出しがタイムアウトした場合は、新しい呼び出しを発行します。 タイムアウト間隔は、の値によって決まりますが、 [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx)のプロパティ、 [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)使用されています。

使用する利点**OnMessage**と比較して**受信**ユーザーが、手動でメッセージのポーリング、例外を処理、並列で複数のメッセージを処理およびメッセージの完了が必要ないことです。

呼び出す場合**受信**せず、その既定値を使用することを確認して、 *ServerWaitTime*値は 1 分以上。 設定*ServerWaitTime*は、メッセージが完全に受信される前に、タイムアウトにより、サーバー 1 分以上にします。

### <a name="solution"></a>ソリューション
推奨される使用状況を次のコード例を参照してください。 詳細については、次を参照してください。 [QueueClient.OnMessage メソッド (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)と[QueueClient.Receive メソッド (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx)します。

Azure のメッセージング インフラストラクチャのパフォーマンスを向上させる、設計パターンを参照してください。[非同期メッセージングの基本](https://msdn.microsoft.com/library/dn589781.aspx)します。

使用する例を次に**OnMessage**メッセージを受信します。

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

使用する例を次に**受信**既定のサーバー待機時間。

```
string connectionString =  
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =  
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)  
{   
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

使用する例を次に**受信**既定以外のサーバー待機時間。

```
while (true)  
{   
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```
## <a name="consider-using-asynchronous-service-bus-methods"></a>Service Bus の非同期メソッドの使用を検討してください。
### <a name="id"></a>ID
AP2003

### <a name="description"></a>説明
仲介型メッセージングでパフォーマンスを向上させるために、Service Bus の非同期メソッドを使用します。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
非同期メソッドを使用すると、メイン スレッドをブロックしない各呼び出しを実行するためにアプリケーション プログラムの同時実行ができます。 Service Bus メッセージング メソッド、操作を実行するを使用する場合 (送信、受信、削除など) は時間がかかります。 この時点には、要求と応答の待機時間だけでなく、Service Bus サービスによって操作の処理が含まれています。 時間あたりの操作の数を増やすには、操作が同時に実行する必要があります。 詳細についてを参照してください[パフォーマンスの機能強化を使用して Service Bus の仲介型メッセージングのベスト プラクティス](https://msdn.microsoft.com/library/azure/hh528527.aspx)します。

### <a name="solution"></a>ソリューション
参照してください[QueueClient クラス (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx)推奨される非同期メソッドを使用する方法についてはします。

Azure のメッセージング インフラストラクチャのパフォーマンスを向上させる、設計パターンを参照してください。[非同期メッセージングの基本](https://msdn.microsoft.com/library/dn589781.aspx)します。

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Service Bus キューおよびトピックをパーティション分割を検討してください。
### <a name="id"></a>ID
AP2004

### <a name="description"></a>説明
パーティションの Service Bus キューと Service Bus メッセージングを使用したパフォーマンス向上のためのトピック。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
Service Bus キューおよびトピックをパーティション分割すると、パーティション分割されたキューまたはトピックの全体的なスループットは 1 つのメッセージ ブローカーまたはメッセージング ストアのパフォーマンスによって制限されなくパフォーマンスのスループットとサービスの可用性が向上します。 さらに、メッセージング ストアが一時的に停止しないパーティション分割されたキューまたはトピックで使用できないようにします。 詳細については、次を参照してください。[メッセージング エンティティのパーティション分割](https://msdn.microsoft.com/library/azure/dn520246.aspx)します。

### <a name="solution"></a>ソリューション
次のコード スニペットでは、メッセージング エンティティをパーティション分割する方法を示します。

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

詳細については、次を参照してください[パーティション分割された Service Bus Queues および Topics |。Microsoft Azure のブログ](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/)とチェック アウト、 [Microsoft Azure Service Bus パーティション分割されたキュー](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f)サンプル。

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime を設定しません。
### <a name="id"></a>ID
AP3001

### <a name="description"></a>説明
現在の時刻に設定された Sharedaccessstarttime を使用して、共有アクセス ポリシーをすぐに開始するを避ける必要があります。 だけ、後で、共有アクセス ポリシーを開始する場合は、このプロパティを設定する必要があります。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
クロックの同期には、データ センター間でわずかな時間差が発生します。 たとえば、論理的と思われる DateTime.Now を使用して、現在の時刻としてストレージの SAS ポリシーの開始時刻を設定または同様のメソッドは、SAS ポリシーをすぐに有効になります。 ただし、データ センター間でわずかな時間の相違点であっても、データ センターも進んで他のユーザーの中に、開始時刻よりもわずかに遅れて場合がありますので、この問題が発生できます。 すぐに (またはすぐに)、SAS ポリシーが有効期限が切れるため、ポリシーの有効期間が短すぎる場合。

Shared Access Signature を使用して Azure storage の詳細については、次を参照してください。 [Introducing Table SAS (Shared Access Signature)、キュー SAS および Blob SAS - Microsoft Azure Storage チーム ブログ - 更新サイトのホーム - MSDN ブログ](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx)します。

### <a name="solution"></a>ソリューション
共有アクセス ポリシーの開始時刻を設定するステートメントを削除します。 Azure コード分析ツールは、この問題の修正プログラムを提供します。 セキュリティ管理の詳細については、デザイン パターンを参照してください[バレット キー パターン](https://msdn.microsoft.com/library/dn568102.aspx)します。

次のコード スニペットでは、この問題に対してコード修正を示します。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>共有アクセス ポリシーの有効期限は 5 分以上である必要があります。
### <a name="id"></a>ID
AP3002

### <a name="description"></a>説明
「クロック スキュー」と呼ばれる状態のためのさまざまな場所にあるデータ センター間でクロックの差が 5 分程度があることができます。 SAS を防ぐために期限切れにならないポリシー トークンは、予定よりも早くを 5 分以上の有効期限を設定します。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
世界各地の異なる場所にあるデータ センターは、クロック信号によって同期されます。 別の場所に移動するクロック信号の時間がかかるため、あります異なる地理的な場所にあるデータ センター間で時間の差異が、すべてが同期されていると思われる。 この時間差は、共有アクセス ポリシーの開始時刻と有効期限間隔に影響を与えます。 そのため、共有アクセス ポリシーは直ちに有効ことを確認するには、開始時刻を指定しないでください。 さらに、有効期限が早期タイムアウトを防ぐために 5 分以上を確認します。

Azure storage での Shared Access Signature の使用に関する詳細については、次を参照してください。 [Introducing Table SAS (Shared Access Signature)、キュー SAS および Blob SAS - Microsoft Azure Storage チーム ブログ - 更新サイトのホーム - MSDN ブログ](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx)します。

### <a name="solution"></a>ソリューション
セキュリティ管理の詳細については、デザイン パターンを参照してください。[バレット キー パターン](https://msdn.microsoft.com/library/dn568102.aspx)します。

次は、共有アクセス ポリシーの開始時刻を指定しない場合の例です。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

次に 5 分以上ポリシーの有効期間と共有アクセス ポリシーの開始時刻を指定する例を示します。

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),   
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

詳細については、次を参照してください。[を作成し、Shared Access Signature を使用して、](https://msdn.microsoft.com/library/azure/jj721951.aspx)します。

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager を使用します。
### <a name="id"></a>ID
AP4000

### <a name="description"></a>説明
使用して、 [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)クラス プロジェクトなど、Azure の web サイトや Azure mobile services は、実行時の問題を導入しません。 ベスト プラクティスとしてがクラウドを使用することをお勧め[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)のすべての Azure クラウド アプリケーションの構成管理の統一された方法として。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
CloudConfigurationManager は、アプリケーション環境に適した構成ファイルを読み取ります。

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>ソリューション
使用するコードをリファクタリング、 [CloudConfigurationManager Class](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)します。 この問題のコード修正は、Azure コード分析ツールによって提供されます。

次のコード スニペットでは、この問題に対してコード修正を示します。 置換

`var settings = ConfigurationManager.AppSettings["mySettings"];`

代入

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

App.config または Web.config ファイルで構成設定を保存する方法の例を次に示します。 設定を構成ファイルの appSettings セクションに追加します。 次に上記のコード例の Web.config ファイルを示します。

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>ハード コーディングされた接続文字列を使用しないでください。
### <a name="id"></a>ID
AP4001

### <a name="description"></a>説明
ハード コーディングされた接続文字列を使用して、それらを後で更新する必要がある場合は、アプリケーションをコンパイルし、ソース コードに変更を加える必要があります。 ただし、構成ファイルに、接続文字列を格納する場合を変更して後で、構成ファイルを更新するだけで。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
ハード コーディングする接続文字列をすばやく変更する必要がある場合は、問題が生じるために、接続文字列が不適切な手法です。 さらに、プロジェクトをソース管理にチェックインする必要がある場合、ソース コードで文字列を表示できるためハード コーディングされた接続文字列にはセキュリティの脆弱性がについて説明します。

### <a name="solution"></a>ソリューション
構成ファイルまたは Azure 環境では、接続文字列を格納します。

* スタンドアロン アプリケーションでは、app.config を使用して、接続文字列の設定を格納します。
* 、IIS でホストされる web アプリケーションの web.config を使用して、接続文字列を格納します。
* ASP.NET vNext アプリケーションでは、configuration.json を使用して、接続文字列を格納します。

Web.config または app.config などの構成ファイルを使用する方法の詳細については、次を参照してください。 [ASP.NET Web 構成のガイドライン](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx)します。 Azure の環境変数の機能については、次を参照してください。 [Azure Web サイト: アプリケーション文字列と接続文字列が機能](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/)します。 ソース管理に接続文字列を格納する方法の詳細については、次を参照してください。[ソース コード リポジトリに格納されているファイルで接続文字列などの機密情報を入れない](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)します。

## <a name="use-diagnostics-configuration-file"></a>診断構成ファイルを使用します。
### <a name="id"></a>ID
AP5000

### <a name="description"></a>説明
Microsoft.WindowsAzure.Diagnostics プログラミング API を使用して、など、コードで診断設定を構成するのではなく、diagnostics.wadcfg ファイルの診断設定を構成する必要があります。 (または、Azure SDK 2.5 を使用する場合は diagnostics.wadcfgx)。 これにより、コードを再コンパイルしなくても診断設定を変更できます。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
前に、Azure SDK 2.5 (Azure 診断 1.3 を使用) する、Azure 診断 (WAD) は、いくつかの方法で構成できました: 命令型コード、宣言型の構成または既定値を使用して、記憶域の構成 blob に追加します。構成します。 ただし、診断を構成することをお勧めは XML 構成ファイル (diagnostics.wadcfg、または SDK 2.5 以降で diagnositcs.wadcfgx)、アプリケーション プロジェクトを使用します。 この方法で diagnostics.wadcfg ファイル完全に構成を定義し更新は再デプロイします。 プログラムによる方法を使用して構成を設定するので、diagnostics.wadcfg 構成ファイルを混在、 [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)または[RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)クラスのことができます混乱する可能性があります。 参照してください[Azure 診断構成の変更の初期化または](https://msdn.microsoft.com/library/azure/hh411537.aspx)詳細についてはします。

以降 (Azure SDK 2.5 に含まれている)、WAD 1.3 では、場合は、コードを使用して診断を構成することがなくなりました。 その結果、適用するか、診断拡張機能を更新するときの構成のみを提供できます。

### <a name="solution"></a>ソリューション
診断構成デザイナーを使用して、診断設定を診断構成ファイル (diagnositcs.wadcfg、または SDK 2.5 以降で diagnositcs.wadcfgx) に移動します。 インストールすることをお勧めも[Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188)最新の診断機能を使用します。

1. 構成するロールのショートカット メニューのプロパティ を選択し、構成 タブをクリックします。
2. **診断**セクションで、ことを確認、**診断の有効化** チェック ボックスをオンします。
3. 選択、**構成**ボタンをクリックします。

   ![診断を有効にするオプションにアクセスします。](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   参照してください[Azure Cloud Services および Virtual Machines 向けの診断の構成](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)詳細についてはします。

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>DbContext オブジェクトを静的として宣言しない.
### <a name="id"></a>ID
AP6000

### <a name="description"></a>説明
メモリを節約するには、DBContext オブジェクトを静的と宣言しないでください。

アイデアやフィードバックを共有してください[Azure コード分析のフィードバック](http://go.microsoft.com/fwlink/?LinkId=403771)します。

### <a name="reason"></a>理由
DBContext オブジェクトは、各呼び出しからのクエリ結果を保持します。 アプリケーション ドメインがアンロードされるまで、静的 DBContext オブジェクトは破棄されません。 そのため、静的 DBContext オブジェクトは、大量のメモリを使用できます。

### <a name="solution"></a>ソリューション
DBContext をローカル変数または非静的インスタンス フィールドとして宣言やタスクで使用し、使用後に破棄するようにします。

MVC コント ローラー クラスの次の例では、DBContext オブジェクトを使用する方法を示します。

```
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext        
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>次の手順
詳細についてを最適化する Azure アプリケーションとトラブルシューティングについては、次を参照してください。 [Visual Studio を使用して Azure App Service で web アプリのトラブルシューティング](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)します。
