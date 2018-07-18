---
title: ワークフロー デザイナーの Send アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 099a512bcbca7136541c9896e32f43b9e518ed8b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978350"
---
# <a name="send-activity-designer"></a>Send アクティビティ デザイナー

**送信**アクティビティ デザイナーを使用して作成し、構成、<xref:System.ServiceModel.Activities.Send>アクティビティ。

## <a name="the-send-activity"></a>Send アクティビティ

 メッセージをサービスに送信するには、<xref:System.ServiceModel.Activities.Send> アクティビティを使用します。 <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、クライアントでの要求/応答メッセージ交換パターンの一部としてメッセージを受信する <xref:System.ServiceModel.Activities.Send> アクティビティにバインドできます。

### <a name="using-the-send-activity-designer"></a>Send アクティビティ デザイナーの使用
 **送信**アクティビティ デザイナーは含まれて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーのタブ (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。

 **送信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**し、アクティビティを通常配置している場所に、ワークフロー デザイナー画面にドロップします。 この操作により、Send という既定の <xref:System.ServiceModel.Activities.Send> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**送信**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

 作成する、<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティに、選択したバインドと<xref:System.ServiceModel.Activities.Send>アクティビティを右クリックし、**送信**アクティビティ デザイナーをクリックして、 **receivereply の作成**コンテキスト メニュー項目の**ReceiveReplyForSend**下デザイナーに表示されます、**送信**デザイナー。 <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、クライアントでの要求/応答メッセージ交換パターンの一部としてメッセージを受信するアクティビティであり、 構成することができます、 **ReceiveReplyForSend**デザイナー。

 または、 **SendAndReceiveReply**テンプレート デザイナー、**メッセージング**のカテゴリ、**ツールボックス**事前構成済みのペアの作成に使用できる<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 使用の詳細については、 **SendAndReceiveReply**と**ReceiveReplyForSend** 、テンプレートを参照してください、 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)トピックです。

### <a name="the-send-activity-properties"></a>Send アクティビティのプロパティ
 次の表に、<xref:System.ServiceModel.Activities.Send> のプロパティと、デザイナーでのその使用方法を示します。 プロパティ グリッドまたはワークフロー デザイナー画面で、これらのプロパティを編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.Send> アクティビティの表示名。 既定値は Send です。 <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|この <xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作の名前。 既定値を構築するためにこのプロパティは使用、**アクション**プロパティ場合、**アクション**プロパティが明示的に設定されていません。|
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|True|呼び出されるサービスが実装するサービス コントラクトの名前。|
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 横にある省略記号ボタンをクリックしてこのプロパティを編集、**コンテンツ**フィールドで、プロパティ グリッドまたはをクリックすると、**定義しています.** ボタンの横にある、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 このボックスを使用する方法の詳細については、次を参照してください。、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピックです。|
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。<br /><br /> 次に省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>を開くにはプロパティ グリッドで、**式エディター**  ダイアログ ボックス。 このダイアログ ボックスの使用に関する詳細については、次を参照してください。、[する方法: 式エディターを使用して](../workflow-designer/how-to-use-the-expression-editor.md)トピックです。|
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Send> オブジェクトのコレクションを指定します。 次に省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>を開くにはプロパティ グリッド内のプロパティ、 **[関連付け初期化子**] ダイアログ ボックス。 詳細については、このボックスを使用して、次を参照してください。、 [CorrelationInitializers ダイアログ ボックスの追加](../workflow-designer/add-correlationinitializers-dialog-box.md)トピックです。|
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|この <xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作の既知の型のコレクション。 このプロパティは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> に設定された <xref:System.Runtime.Serialization.DataContractSerializer> プロパティと共に使用する必要があります。 <xref:System.Xml.Serialization.XmlSerializer> が使用されている場合は無視されます。<br /><br /> 横にある省略記号ボタンをクリックして、 **KnownTypes**フィールドを表示するプロパティ グリッドで、**型コレクション エディター**ダイアログを使用するには、関連する型を追加することができます。<br /><br /> 横にある省略記号ボタンをクリックして、 **KnownTypes**フィールドを表示するプロパティ グリッドで、**型コレクション エディター**  ダイアログ ボックスを使用するには、関連する型を追加することができます。 詳細については、このボックスを使用して、次を参照してください。、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピックです。|
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|True|メッセージの <xref:System.Net.Security.ProtectionLevel> を指定します。<br /><br /> 1。<xref:System.Net.Security.ProtectionLevel>認証のみを意味します。<br />2。<xref:System.Net.Security.ProtectionLevel>署名データ送信されるデータの整合性を確保することを意味します。<br />3。<xref:System.Net.Security.ProtectionLevel>手段の暗号化と署名データを送信されるデータの整合性と機密性を確保します。|
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|True|<xref:System.ServiceModel.Activities.Send> アクティビティによって呼び出されるサービス操作に使用するシリアライザー。 既定値は <xref:System.Runtime.Serialization.DataContractSerializer> です。このシリアライザーは、ある型のインスタンスを、提供されたデータ コントラクトを使用する XML ストリームまたはドキュメントへとシリアル化または逆シリアル化します。|
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|メッセージのアクション ヘッダーを指定します。 これが明示的に設定されていない場合、既定値を:https://tempuri.org/{serviceコントラクトの名前空間}/{サービス コントラクト名}/{操作名}。 <xref:System.ServiceModel.Activities.Send> アクティビティで指定した場合は、メッセージを正しく配信するために、メッセージを受信する <xref:System.ServiceModel.Activities.Receive> アクティビティに同じ値を設定する必要があります。|
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||メッセージの受信側に許可される <xref:System.Security.Principal.TokenImpersonationLevel>。 サーバー プロセスがクライアント プロセスの代理として動作できる程度を制御するセキュリティ偽装レベルを定義します。<xref:System.Security.Principal.TokenImpersonationLevel> 権限借用レベルが割り当てられていないことを示します。 <xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがクライアントの識別情報を取得することも、クライアントを偽装することもできないことを示します。 <xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがセキュリティ ID や特権などのクライアント情報を取得できるが、クライアントを偽装できないことを示します。 これは、テーブルとビューをエクスポートするデータベース製品など、独自のオブジェクトをエクスポートするサーバーで役立ちます。 サーバーは、このクライアントのセキュリティ コンテキストを使用する他のサービスを使用できなくても、取得したクライアントのセキュリティ情報を使用してアクセス検証に関する決定を行うことができます。 <xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがローカル システム上にあるクライアントのセキュリティ コンテキストを偽装できることを示します。 サーバーは、リモート システムにあるクライアントを偽装できません。 <xref:System.Security.Principal.TokenImpersonationLevel> は、サーバー プロセスがリモート システム上にあるクライアントのセキュリティ コンテキストを偽装できることを示します。|
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint> アクティビティによるメッセージの送信先の <xref:System.ServiceModel.Activities.Send>。 このプロパティが設定されている場合、<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>プロパティにする必要があります**null**です。|
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||メッセージの送信先となる <xref:System.ServiceModel.EndpointAddress>。|
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||エンドポイント構成の名前。 このプロパティは、エンドポイントを構成ファイルで構成している場合に設定します。 このプロパティで指定された名前に設定する必要があります、 **\<エンドポイント >** 構成ファイル内の要素。 このプロパティが設定されている場合、<xref:System.ServiceModel.Activities.Send.Endpoint%2A>プロパティにする必要があります**null**です。|

## <a name="see-also"></a>関連項目

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [受信](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)