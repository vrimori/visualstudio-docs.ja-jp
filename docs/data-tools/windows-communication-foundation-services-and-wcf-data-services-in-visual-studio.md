---
title: "Windows Communication Foundation サービスと Visual Studio での WCF Data Services |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 39c9ac7b1cbed8c64ee3b87fde4c990f998157a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio での Windows Communication Foundation サービスと WCF データ サービス
Visual Studio には、Windows Communication Foundation (WCF) を操作するためのツールが用意されていて、 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、分散アプリケーションを作成するための Microsoft テクノロジです。 このトピックでは、サービスからの概要、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パースペクティブです。 完全なドキュメントを参照してください。 [WCF データ サービス 4.5](/dotnet/framework/data/wcf/index)です。  
  
## <a name="what-is-wcf"></a>WCF とは何ですか。  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]セキュリティで保護された、信頼性、トランザクション、および相互運用可能な分散アプリケーションを作成するための統一フレームワークです。 ASMX Web サービス、.NET リモート処理、エンタープライズ サービス (DCOM)、および MSMQ などの以前のプロセス間通信テクノロジに置き換えます。 WCF は、統一されたプログラミング モデルでこれらすべてのテクノロジの機能をまとめます。 これにより、分散アプリケーションの開発のエクスペリエンスが合理化されます。  
  
#### <a name="what-are-wcf-data-services"></a>WCF Data Services とは  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Open Data (OData) プロトコルの実装は標準です。  WCF Data Services では、表形式データなどの標準の HTTP 動詞を使用してデータの取得を返す、POST、PUT または DELETE することができます、REST Api のセットとして公開することができます。 サーバー側では、WCF Data Services は、中に置き換えられて[ASP.NET Web API](http://www.asp.net/web-api)新しい OData サービスを作成します。 WCF Data Services クライアント ライブラリは引き続き Visual Studio からの .NET アプリケーションでの OData サービスの使用に適して (**プロジェクト &#124;です。サービス参照の追加**)。 詳細については、次を参照してください。 [WCF データ サービス 4.5](http://go.microsoft.com/fwlink/?LinkID=119952)です。  
  
### <a name="wcf-programming-model"></a>WCF プログラミング モデル  
 WCF プログラミング モデルは 2 つのエンティティ間の通信に基づく: WCF サービスと WCF クライアントです。 プログラミング モデルにカプセル化されて、<xref:System.ServiceModel>で名前空間、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。  
  
#### <a name="wcf-service"></a>WCF サービス  
 WCF サービスは、サービスとクライアント間のコントラクトを定義するインターフェイスに基づいています。 設定されて、<xref:System.ServiceModel.ServiceContractAttribute>属性が次のコードに示すようにします。  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 関数またはでそれらをマークすることによって、WCF サービスによって公開されるメソッドを定義する、<xref:System.ServiceModel.OperationContractAttribute>属性。 さらに、シリアル化されたデータを公開と複合型をマークすることによって、<xref:System.Runtime.Serialization.DataContractAttribute>属性。 これにより、クライアントでのデータ バインドできます。  
  
 インターフェイスとそのメソッドを定義した後は、インターフェイスを実装するクラスにカプセル化します。 1 つの WCF サービス クラスには、複数のサービス コントラクトを実装できます。  
  
 新機能を使用して利用と呼ばれますの WCF サービスが公開される、*エンドポイント*です。 エンドポイントは、サービスと通信する唯一の方法他のクラスと同様に、直接の参照を使用してサービスにアクセスすることはできません。  
  
 エンドポイントは、アドレス、バインディング、およびコントラクトで構成されます。 アドレスは、サービスが存在します。 場所を定義しますURL、FTP アドレス、またはネットワークまたはローカル パスが考えられます。 バインディングでは、サービスと通信する方法を定義します。 WCF バインディングが HTTP または FTP では、Windows 認証またはユーザー名やパスワードなど、セキュリティ メカニズムなどのプロトコルを指定するために汎用的なモデルを提供し、はるかにします。 コントラクトには、WCF サービス クラスによって公開されている操作が含まれます。  
  
 1 つの WCF サービスに対して複数のエンドポイントを公開することができます。 これにより、さまざまな方法で同一のサービスと通信するためにさまざまなクライアントです。 たとえば、銀行のサービスは、1 つのエンドポイント従業員およびその他のお客様に提供する外部、別のアドレス、バインドを使用して各や、コントラクトします。  
  
#### <a name="wcf-client"></a>WCF クライアント  
 WCF クライアントから成る、*プロキシ*WCF サービスと通信するためにアプリケーションを有効にして、サービスのエンドポイントに一致するエンドポイントが定義されています。 プロキシは、app.config ファイルでクライアント側で生成され、サービスによって公開されるメソッドと型に関する情報が含まれています。 複数のエンドポイントを公開するサービス、クライアントが HTTP 経由で通信、Windows 認証を使用して、ニーズに最適な 1 つを選択できます。  
  
 WCF クライアントを作成した後は、他のオブジェクトと同様に、コード内でサービスを参照します。 例についてを呼び出して、`GetData`メソッドは、次のようなコードを記述する前に示した。  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Visual Studio での WCF ツール  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]WCF サービスと WCF クライアントの両方を作成するのに役立つツールを提供します。 ツールについて説明するチュートリアルでは、次を参照してください。[チュートリアル: Windows フォームでの簡単な WCF サービスの作成](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)です。  
  
### <a name="creating-and-testing-wcf-services"></a>作成して WCF サービスをテストします。  
 WCF を使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]独自のサービスをすばやく作成する基礎としてテンプレート。 デバッグして、サービスをテストし、WCF サービスの自動ホストと WCF テスト クライアントを使用できます。 これらのツールは一緒に高速で簡単なデバッグとテストのサイクルを入力し、早い段階でホスト モデルにコミットする必要があります。  
  
#### <a name="wcf-templates"></a>WCF テンプレート  
 WCF[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テンプレートがサービスの開発の基本クラス構造を提供します。 いくつかの WCF テンプレートで使用できる、**新しいプロジェクトの追加** ダイアログ ボックス。 WCF サービス ライブラリ プロジェクト、WCF サービスの Web サイト、および WCF サービス項目テンプレートが含まれます。  
  
 テンプレートを選択すると、サービス コントラクト、サービス実装、およびサービス構成ファイルが追加されます。 必要な属性が既に追加されて、サービスの単純な"Hello World"型を作成して、コードを記述する必要はありません。 関数と実際のサービスのメソッドを提供するためのコードを追加することが、もちろんが、テンプレートは、基本的な基盤を提供します。  
  
 WCF テンプレートの詳細については、次を参照してください。 [WCF Visual Studio テンプレート](/dotnet/framework/wcf/wcf-vs-templates)です。  
  
#### <a name="wcf-service-host"></a>WCF サービス ホスト  
 開始すると、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (f5 キーを押して) デバッガーの WCF サービス プロジェクトの場合、WCF サービス ホストのローカルでサービスをホストするツールが自動的に起動します。 WCF サービス ホストは、WCF サービス プロジェクト内のサービスを列挙、プロジェクトの構成が読み込まれ、検出された各サービスのホストのインスタンスを作成します。  
  
 WCF サービス ホストを使用すると、余分なコードを記述したり、開発時に特定のホストにコミットすることがなく、WCF サービスをテストできます。  
  
 WCF サービス ホストの詳細については、次を参照してください。 [WCF サービス ホスト (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)です。  
  
#### <a name="wcf-test-client"></a>WCF のテスト用クライアント  
 WCF テスト クライアント ツールでは、テスト パラメーターを入力し、WCF サービスへの入力を送信することができ、サービスを返信する応答を表示します。 WCF サービス ホストと結合するときのエクスペリエンスのテストの便利なサービスを提供します。 ここでは、c: ドライブにインストールされている Visual Studio 2015 用を \Common7\IDE フォルダーに、ツールが見つかりません: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**です。  
  
 WCF サービス プロジェクトをデバッグする場合は F5 キーを押したときに WCF テスト クライアントが開き、構成ファイルで定義されているサービス エンドポイントの一覧が表示されます。 パラメーターをテスト サービスを開始し、継続的にテストし、サービスを検証するには、このプロセスを繰り返します。  
  
 WCF テスト クライアントの詳細については、次を参照してください。 [WCF テスト クライアント (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)です。  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio での WCF サービスへのアクセス  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロキシとを使用して追加するサービスのエンドポイントを自動的に生成する、WCF クライアントを作成するタスクを簡略化、**サービス参照の追加** ダイアログ ボックス。 すべての必要な構成情報は、app.config ファイルに追加されます。 ほとんどを行う必要があるインスタンス化するサービスそれを使用するためにします。  
  
 **サービス参照の追加**ダイアログ ボックスで、サービスのアドレスを入力するか、ソリューションで定義されているサービスを検索できます。 ダイアログ ボックスでは、サービスとそれらのサービスによって提供される操作の一覧を返します。 これによってコード内でサービスを参照する名前空間を定義することもできます。  
  
 **サービス参照の構成** ダイアログ ボックスでは、サービスの構成をカスタマイズすることができます。 サービスのアドレスの変更をアクセス レベル、非同期動作は、メッセージ コントラクト型を指定して、型の再利用を構成することができます。  
  
## <a name="how-to-select-a-service-endpoint"></a>方法: サービス エンドポイントを選択  
一部の Windows Communication Foundation (WCF) サービスは、使用するクライアントがサービスと通信可能性があります複数のエンドポイントを公開します。 たとえば、サービスは HTTP バインドとユーザー名を使用する 1 つのエンドポイントを公開する可能性があります/パスワードのセキュリティと FTP と Windows 認証を使用する 2 番目のエンドポイント。 一方、2 番目はイントラネットで使用可能性があります、最初のエンドポイントをファイアウォールの外側からサービスにアクセスするアプリケーションで使用可能性があります。  
  
このような場合を指定できます、`endpointConfigurationName`サービス参照のコンス トラクターにパラメーターとして。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>サービス エンドポイントを選択するには  
  
1.  ソリューション エクスプ ローラーでプロジェクト ノードを右クリックして、WCF サービスへの参照を追加**サービス参照の追加**です。
  
2.  コード エディターでは、サービス参照のコンス トラクターを追加します。  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  置き換える*ServiceReference*サービス参照の追加と置換の名前空間を持つ*Service1Client*サービスの名前に置き換えます。  
  
3.  コンス トラクターのオーバー ロードは、IntelliSense の一覧が表示されます。 選択、`endpointConfigurationName As String`オーバー ロードします。  
  
4.  次のオーバー ロードは、次のように入力します。 `=` *ConfigurationName*ここで、 *ConfigurationName*を使用するエンドポイントの名前を指定します。  
  
    > [!NOTE]
    >  使用可能なエンドポイントの名前がわからない場合は、app.config ファイルで確認できます。  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF サービスの利用可能なエンドポイントが見つかりません  
  
1.  **ソリューション エクスプ ローラー**サービス参照を含むプロジェクトの app.config ファイルを右クリックし、クリックして**開く**です。 ファイルは、コード エディターに表示されます。  
  
2.  検索、`<Client>`ファイル内のタグ。  
  
3.  下にある検索、`<Client>`で始まるタグのタグを`<Endpoint>`です。  
  
     サービス参照は、複数のエンドポイントを提供する場合があります複数`<Endpoint`タグ。  
  
4.  内部、`<EndPoint>`タグが表示されます、 `name="` *SomeService* `"`パラメーター (ここで*SomeService*エンドポイント名を表します)。 これに渡すことができるエンドポイントの名前、`endpointConfigurationName As String`サービス参照のコンス トラクターのオーバー ロードします。  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>方法: 非同期サービス メソッドを呼び出す  
Windows Communication Foundation (WCF) サービスのほとんどのメソッドは、同期または非同期で呼び出すことができます。 非同期のメソッドを呼び出すには、低速接続で実行しているときに、メソッドが呼び出されるときに作業を続行するアプリケーションができるようにします。  
  
既定では、サービスの参照がプロジェクトに追加されたときに同期的にメソッドの呼び出しに構成されます。 設定を変更するメソッドを非同期に呼び出すに動作を変更することができます、**サービス参照の構成** ダイアログ ボックス。  
  
> [!NOTE]
>  このオプションは、サービスごとに設定されます。 サービスのメソッドの 1 つは非同期的に呼び出されると、すべてのメソッドを非同期的に呼び出す必要があります。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>サービス メソッドを非同期的に呼び出す  
  
1.  **ソリューション エクスプ ローラー**、サービス参照を選択します。  
  
2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**です。  
  
3.  **サービス参照の構成**ダイアログ ボックスで、**非同期操作を生成する**チェック ボックスをオンします。  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>方法: サービスによって返されるデータのバインド  
その他のデータ ソースをコントロールにバインドすると同様、コントロールに Windows Communication Foundation (WCF) サービスによって返されるデータをバインドすることができます。 追加すると、WCF サービスへの参照をサービスにデータを取得する複合型が含まれている場合、ユーザーは自動的に追加、**データソース**ウィンドウです。  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WCF サービスによって返された 1 つのデータ フィールドにコントロールをバインドするには  
  
1.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。 **データソース**ウィンドウが表示されます。  
  
2.  **データソース**ウィンドウで、サービス参照のノードを展開します。 サービスによって返される、複合型が表示されます。  
  
3.  型のノードを展開します。 その型のデータ フィールドが表示されます。  
  
4.  フィールドを選択し、データ型の使用可能なコントロールの一覧を表示するドロップダウン矢印をクリックします。  
  
5.  バインドするコントロールの種類をクリックします。  
  
6.  フィールドをフォームにドラッグします。 コントロールと共にフォームに追加されます、<xref:System.Windows.Forms.BindingSource>コンポーネントおよび<xref:System.Windows.Forms.BindingNavigator>コンポーネントです。  
  
7.  手順 4. を繰り返して他のフィールドがバインドします。  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF サービスによって返される複合型にコントロールをバインドするには  
  
1.  **データ**メニューの **データ ソースの表示**です。 **データソース**ウィンドウが表示されます。  
  
2.  **データソース**ウィンドウで、サービス参照のノードを展開します。 サービスによって返される、複合型が表示されます。  
  
3.  型のノードを選択し、使用可能なオプションの一覧を表示するドロップダウン矢印をクリックします。  
  
4.  いずれかをクリックして**DataGridView**グリッドに、データを表示または**詳細**個々 のコントロールにデータを表示します。  
  
5.  ノードをフォームにドラッグします。 コントロールと共にフォームに追加されます、<xref:System.Windows.Forms.BindingSource>コンポーネントおよび<xref:System.Windows.Forms.BindingNavigator>コンポーネントです。  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>方法: 既存の型を再利用するサービスを構成します。  
サービス参照がプロジェクトに追加されると、サービスで定義された任意の型は、ローカル プロジェクトで生成されます。 多くの場合、重複する型と作成サービスを使用して一般的な[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型または型が、共有ライブラリで定義されている場合。  
  
この問題を回避するのには、参照されたアセンブリで型が既定で共有されます。 型の 1 つまたは複数のアセンブリの共有を無効にする場合は、行うことができますに、**サービス参照の構成** ダイアログ ボックス。  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>1 つのアセンブリで型の共有を無効にするには  
  
1.  **ソリューション エクスプ ローラー**、サービス参照を選択します。  
  
2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**です。  
  
3.  **サービス参照の構成**ダイアログ ボックスで、**指定された参照されたアセンブリで型を再利用**です。  
  
4.  型の共有を有効にする各アセンブリのチェック ボックスを選択します。 型のアセンブリの共有を無効にするには、チェック ボックスをオフのままにします。  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>すべてのアセンブリで型の共有を無効にするには  
  
1.  **ソリューション エクスプ ローラー**、サービス参照を選択します。  
  
2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**です。  
  
3.  **サービス参照の構成**ダイアログ ボックスで、クリア、**参照されたアセンブリで型を再利用**チェック ボックスをオンします。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル : Windows フォームでの簡単な WCF サービスの作成](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|ステップ バイ ステップの作成と使用で WCF サービスのデモンストレーションを行います[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。|  
|[チュートリアル: WPF と Entity Framework を使用した WCF データ サービスの作成](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|作成および使用する方法の詳細な手順のデモンストレーションを行います[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]で[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。|  
|[WCF 開発ツールの使用](/dotnet/framework/wcf/using-the-wcf-development-tools)|作成し、WCF サービスをテストする方法について説明[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。|  
||[方法: WCF データ サービス参照を追加、更新、または削除する](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|参照および使用する方法について説明[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]で[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。|  
|[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)|サービスの参照とその回避方法、発生することがいくつかの一般的なエラーを表示します。|  
|[WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)|共通の問題のデバッグと WCF サービスをデバッグするときに発生する可能性が手法について説明します。|  
|[Windows Communication Foundation 認証サービスの概要](http://msdn.microsoft.com/Library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|WCF を使用して Web サイトの役割サービスを提供する方法について説明します。|  
|[チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|型指定されたデータセットを作成し、TableAdapter とデータセット コードを複数のプロジェクトに分離する手順について説明します。|  
|[[サービス参照の構成] ダイアログ ボックス](../data-tools/configure-service-reference-dialog-box.md)|ユーザー インターフェイス要素について説明します、**サービス参照の構成** ダイアログ ボックス。|  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)