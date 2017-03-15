---
title: "Send アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.Send.UI"
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Send アクティビティ デザイナー
**Send** アクティビティ デザイナーは、<xref:System.ServiceModel.Activities.Send> アクティビティを作成および構成するために使用します。  
  
## Send アクティビティ  
 メッセージをサービスに送信するには、<xref:System.ServiceModel.Activities.Send> アクティビティを使用します。<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、クライアントでの要求\/応答メッセージ交換パターンの一部としてメッセージを受信する <xref:System.ServiceModel.Activities.Send> アクティビティにバインドできます。  
  
### Send アクティビティ デザイナーの使用  
 **Send** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Send** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の任意の画面にドロップできます。この操作により、Send という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.ServiceModel.Activities.Send> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**Send** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
 <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティを作成し、選択した <xref:System.ServiceModel.Activities.Send> アクティビティにバインドするには、**Send** アクティビティ デザイナーを右クリックし、コンテキスト メニューの **\[ReceiveReply の作成\]** をクリックします。これで、**Send** デザイナーの下に **ReceiveReplyForSend** デザイナーが表示されます。<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、クライアントでの要求\/応答メッセージ交換パターンの一部としてメッセージを受信するアクティビティであり、**ReceiveReplyForSend** デザイナーで構成できます。  
  
 また、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリの **SendAndReceiveReply** テンプレート デザイナーを使用して、定義済みの <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティのペアを作成できます。**SendAndReceiveReply** と **ReceiveReplyForSend** テンプレートの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)」を参照してください。  
  
### Send アクティビティのプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.Send> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.Send> アクティビティの表示名。既定値は Send です。<xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|必須|この <xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作の名前。このプロパティは、**Action** プロパティが明示的に設定されていない場合に、**Action** プロパティの既定値を構成するために使用します。|  
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|必須|呼び出されるサービスが実装するサービス コントラクトの名前。|  
|<xref:System.ServiceModel.Activities.Send.Content%2A>|省略可|受信するメッセージまたはパラメーターの内容を指定します。<xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。このプロパティを編集するには、プロパティ グリッドで **\[Content\]** フィールドの横にある省略記号ボタンをクリックするか、**Receive** アクティビティ デザイナー画面で "**コンテンツ**" というラベルの横にある **\[定義\]** ボタンをクリックします。両方で **\[コンテンツ定義\]** ダイアログが表示されます。このダイアログ ボックスの使用方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[コンテンツ定義\] ダイアログ ボックス](../Topic/Content%20Definition%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|省略可|適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。<br /><br /> プロパティ グリッドで <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> プロパティの横にある省略記号ボタンをクリックして、**\[式エディター\]** ダイアログ ボックスを開きます。このダイアログ ボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[式エディターを使用する方法](../workflow-designer/how-to-use-the-expression-editor.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|省略可|ワークフロー内のこの <xref:System.ServiceModel.Activities.Send> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.CorrelationInitializer> オブジェクトのコレクションを指定します。プロパティ グリッドで <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> プロパティの横にある省略記号ボタンをクリックして、**\[関連付け初期化子の追加\]** ダイアログ ボックスを開きます。このボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[関連付け初期化子の追加\] ダイアログ ボックス](../Topic/Add%20CorrelationInitializers%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|省略可|この <xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作の既知の型のコレクション。このプロパティは、<xref:System.Runtime.Serialization.DataContractSerializer> に設定された <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティと共に使用する必要があります。<xref:System.Xml.Serialization.XmlSerializer> が使用されている場合は無視されます。<br /><br /> プロパティ グリッドで **\[KnownTypes\]** フィールドの横にある省略記号ボタンをクリックして、**\[型コレクション エディター\]** ダイアログを開きます。このダイアログで、該当する型を追加できます。<br /><br /> プロパティ グリッドで **KnownTypes** フィールドの横にある省略記号ボタンをクリックして、**\[型コレクション エディター\]** ダイアログ ボックスを開きます。このダイアログで、該当する型を追加できます。このボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[型コレクション エディター\] ダイアログ ボックス](../Topic/Type%20Collection%20Editor%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|必須|メッセージの <xref:System.Net.Security.ProtectionLevel> を指定します。<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> は、認証のみを意味します。<br />2.  <xref:System.Net.Security.ProtectionLevel> は、送信されるデータの整合性の確保に役立つ署名データを意味します。<br />3.  <xref:System.Net.Security.ProtectionLevel> は、送信されるデータの機密性と整合性の確保に役立つ暗号化と署名データを意味します。|  
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|必須|<xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作に使用するシリアライザー。既定値は <xref:System.Runtime.Serialization.DataContractSerializer> です。このシリアライザーは、ある型のインスタンスを、提供されたデータ コントラクトを使用する XML ストリームまたはドキュメントへとシリアル化または逆シリアル化します。|  
|<xref:System.ServiceModel.Activities.Send.Action%2A>|省略可|メッセージのアクション ヘッダーを指定します。これを明示的に設定しない場合は、既定値の https:\/\/tempuri.org\/\<サービス コントラクトの名前空間\>\/\<サービス コントラクト名\>\/\<操作名\> が設定されます。<xref:System.ServiceModel.Activities.Send> アクティビティで指定した場合は、メッセージを正しく配信するために、メッセージを受信する <xref:System.ServiceModel.Activities.Receive> アクティビティに同じ値を設定する必要があります。|  
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||メッセージの受信側に許可される <xref:System.Security.Principal.TokenImpersonationLevel>。サーバー プロセスがクライアント プロセスの代わりに動作できる程度を制御するセキュリティ偽装レベルを定義します。<xref:System.Security.Principal.TokenImpersonationLevel> は、偽装レベルが割り当てられていないことを示します。<xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがクライアントの識別情報を取得することも、クライアントを偽装することもできないことを示します。<xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがセキュリティ ID や特権などのクライアント情報を取得できるが、クライアントを偽装できないことを示します。これは、テーブルとビューをエクスポートするデータベース製品など、独自のオブジェクトをエクスポートするサーバーで役立ちます。サーバーは、このクライアントのセキュリティ コンテキストを使用する他のサービスを使用できなくても、取得したクライアントのセキュリティ情報を使用してアクセス検証に関する決定を行うことができます。<xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがローカル システム上にあるクライアントのセキュリティ コンテキストを偽装できることを示します。サーバーは、リモート システムにあるクライアントを偽装できません。<xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがリモート システム上にあるクライアントのセキュリティ コンテキストを偽装できることを示します。|  
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Activities.Send> アクティビティによるメッセージの送信先の <xref:System.ServiceModel.Endpoint>。このプロパティを設定した場合は、<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> プロパティが **null** である必要があります。|  
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||メッセージの送信先となる <xref:System.ServiceModel.EndpointAddress>。|  
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||エンドポイント構成の名前。このプロパティは、エンドポイントを構成ファイルで構成している場合に設定します。このプロパティは、構成ファイルの **\<endpoint\>** 要素で指定されている名前に設定する必要があります。このプロパティを設定した場合は、<xref:System.ServiceModel.Activities.Send.Endpoint%2A> プロパティが **null** である必要があります。|  
  
## 参照  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)