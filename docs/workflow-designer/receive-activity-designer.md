---
title: ワークフロー デザイナーの Receive アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c75b635cbdce7662c9e3a30237edb3e004ab7d0c
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742444"
---
# <a name="receive-activity-designer"></a>Receive アクティビティ デザイナー

**受信**作成および構成するアクティビティ デザイナーが使用される、<xref:System.ServiceModel.Activities.Receive>アクティビティ。 <xref:System.ServiceModel.Activities.Receive> アクティビティは、メッセージ (<xref:System.ServiceModel.Channels.Message>、<xref:System.IO.Stream>、<xref:System.Xml.Linq.XElement> などの組み込みの型、アプリケーション定義のデータ コントラクト、メッセージ コントラクト、またはシリアル化可能な XML クラス) を受信するアクティビティです。

## <a name="the-receive-activity"></a>Receive アクティビティ

<xref:System.ServiceModel.Activities.Receive> アクティビティでは、使用されている受信コンテンツの型に応じて、単一または複数のアイテムを受信できます。 <xref:System.ServiceModel.Activities.SendReply> アクティビティは、サービスでの要求/応答メッセージ交換パターンの一部としてメッセージを受信する <xref:System.ServiceModel.Activities.Receive> アクティビティにバインドできます。

### <a name="using-the-receive-activity-designer"></a>Receive アクティビティ デザイナーの使用

アクセス、**受信**内のアクティビティ デザイナー、**メッセージング**のカテゴリ、**ツールボックス**します。 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを通常配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**受信**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

作成する、<xref:System.ServiceModel.Activities.SendReply>アクティビティに、選択したバインドと<xref:System.ServiceModel.Activities.Receive>アクティビティを右クリックし、**受信**アクティビティ デザイナー、 をクリックして、 **SendReply の作成**コンテキスト メニューの項目、**SendReplyToReceive**下デザイナーに表示されます、**受信**デザイナー。 <xref:System.ServiceModel.Activities.SendReply> アクティビティは、サービスでの要求/応答メッセージ交換パターンの一部として応答メッセージを送信するアクティビティであり、 構成できますが、 **SendReplyToReceive**デザイナー。

または、 **ReceiveAndSendReply**テンプレート デザイナーで、**メッセージング**のカテゴリ、**ツールボックス**の事前構成済みのペアを作成するために使用する<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>アクティビティ。 使用の詳細については、 **ReceiveAndSendReply**と**SendReplyToReceive**テンプレートを参照してください、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)トピック。

### <a name="the-receive-activity-properties"></a>Receive アクティビティのプロパティ

次の表に、<xref:System.ServiceModel.Activities.Receive> のプロパティと、デザイナーでのその使用方法を示します。 プロパティ グリッドで、またはワークフロー デザイナー画面で、これらのプロパティを編集できます。 必須のプロパティは <xref:System.ServiceModel.Activities.Receive.OperationName%2A> プロパティのみです。


| プロパティ名 | 必須 | 使用方法 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.Receive> アクティビティの表示名を指定します。 既定値は Receive です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。 |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | この <xref:System.ServiceModel.Activities.Receive> アクティビティによって実装されるサービス操作の名前を指定します。 このプロパティを使用して構築の既定値を**アクション**プロパティ場合、**アクション**プロパティが明示的に設定されていません。 |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | サービス コントラクトの名前を指定します。 このプロパティは、サービス操作を個々のサービス コントラクトにグループ化するために使用します。 同じ <xref:System.ServiceModel.Activities.Receive> を持つすべての <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> アクティビティは、同じサービス コントラクト (WSDL ポートの種類) にグループ化されます。 既定値は、最上位レベル (ルート) アクティビティの完全修飾 CLR 名です。 |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | 受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 このプロパティの横にある省略記号ボタンを選択して編集、**コンテンツ**フィールドにプロパティ グリッドまたはをクリックすると、**定義しています.** ボタンの横にある、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 このボックスを使用する方法の詳細については、次を参照してください。、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | <xref:System.ServiceModel.Activities.Receive> オブジェクトを持つワークフローのサービス操作における <xref:System.ServiceModel.MessageQuerySet> アクティビティ間の相関関係を指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>プロパティを開く [プロパティ] グリッドで、 **[CorrelatesOn の定義**] ダイアログ ボックス。 このダイアログ ボックスの使用に関する詳細については、次を参照してください。、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | 適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。<br /><br /> 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>プロパティを開く プロパティ グリッドで、**式エディター**  ダイアログ ボックス。 このダイアログ ボックスの使用に関する詳細については、次を参照してください。、[方法。式エディターを使用して](../workflow-designer/how-to-use-the-expression-editor.md)トピック。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>プロパティを開く [プロパティ] グリッドで、 **[関連付け初期化子**] ダイアログ ボックス。 詳細については、このボックスを使用して、次を参照してください。、[関連付け初期化子の追加 ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | メッセージが既存のワークフロー インスタンスと関連付けられていない場合に、新しいワークフロー インスタンスを作成して、このメッセージを処理するかどうかを決定する値を指定します。 値が設定されている場合**true**メッセージが既存のワークフロー インスタンスに関連付けられていない場合は、メッセージを処理する新しいワークフロー インスタンスが作成されます。 |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | この <xref:System.ServiceModel.Activities.Receive> アクティビティによって実装されるサービス操作の既知の型のコレクションを指定します。 このプロパティは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> に設定された <xref:System.Runtime.Serialization.DataContractSerializer> プロパティと共に使用する必要があり、 <xref:System.Xml.Serialization.XmlSerializer> が使用されている場合は無視されます。<br /><br /> 横にある省略記号ボタンを選択して、 **KnownTypes**プロパティ グリッドでフィールド、**型コレクション エディター**  ダイアログ ボックスの関連する型を追加できます。 詳細については、このボックスを使用して、次を参照してください。、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | メッセージの <xref:System.Net.Security.ProtectionLevel> を指定します。<br /><br /> 1。<xref:System.Net.Security.ProtectionLevel>認証のみを意味します。<br />2。<xref:System.Net.Security.ProtectionLevel>署名データ送信されるデータの整合性を確保することを意味します。<br />3。<xref:System.Net.Security.ProtectionLevel>手段の暗号化と機密性と送信されるデータの整合性を確保するデータに署名します。 |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | <xref:System.ServiceModel.Activities.Receive> アクティビティによって実装されるサービス操作に使用するシリアライザーの型を指定します。 既定値は <xref:System.Runtime.Serialization.DataContractSerializer> です。この場合、ある型のインスタンスが、提供されたデータ コントラクトを使用する XML ストリームまたはドキュメントへとシリアル化または逆シリアル化されます。 XML をより厳密に制御する必要がある場合は、<xref:System.Xml.Serialization.XmlSerializer> も使用できます。 |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | メッセージのアクション ヘッダーを指定します。 明示的に設定されていない場合に、既定値:`https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`します。 |

## <a name="see-also"></a>関連項目

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
