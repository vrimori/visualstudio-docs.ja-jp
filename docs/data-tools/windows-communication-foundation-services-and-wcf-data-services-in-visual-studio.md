---
title: Visual Studio での Windows Communication Foundation サービスと WCF データ サービス
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 197418bc1a4f8049c0388af005ef36eff287a856
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915933"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio での Windows Communication Foundation サービスと WCF データ サービス
Visual Studio には、Windows Communication Foundation (WCF) を操作するためのツールが用意されていて、 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、分散アプリケーションを作成するための Microsoft テクノロジです。 このトピックでは、Visual Studio の観点からサービスの概要を説明します。 完全なドキュメントについては、次を参照してください。 [WCF データ サービスの 4.5](/dotnet/framework/data/wcf/index)します。

## <a name="what-is-wcf"></a>WCF とは何ですか。
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] セキュリティで保護された、信頼性が高く、トランザクション、および相互運用可能な分散アプリケーションを作成するための統一されたフレームワークです。 ASMX web サービス、.NET リモート処理、エンタープライズ サービス (DCOM)、および MSMQ などの以前のプロセス間通信テクノロジを置き換えます。 WCF は、統一されたプログラミング モデルでこれらすべてのテクノロジの機能です。 これは、分散アプリケーションの開発のエクスペリエンスを簡略化します。

### <a name="what-are-wcf-data-services"></a>WCF Data Services とは
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 標準的な Open Data (OData) プロトコルの実装です。  WCF Data Services では、表形式のデータを返すなどの標準的な HTTP 動詞を使用してデータの取得、投稿、PUT、または削除することができます、REST Api のセットとして公開できます。 によって、サーバー側で WCF Data Services が置き換えられる[ASP.NET Web API](http://www.asp.net/web-api)新しい OData サービスを作成します。 WCF Data Services のクライアント ライブラリは Visual Studio からの .NET アプリケーションで OData サービスの使用に適して (**プロジェクト&#124;サービス参照の追加**)。 詳細については、次を参照してください。 [WCF データ サービスの 4.5](http://go.microsoft.com/fwlink/?LinkID=119952)します。

### <a name="wcf-programming-model"></a>WCF プログラミング モデル
 WCF プログラミング モデルは 2 つのエンティティ間の通信に基づいて: WCF サービスと WCF クライアントです。 プログラミング モデルにカプセル化、<xref:System.ServiceModel>で名前空間、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]します。

### <a name="wcf-service"></a>WCF サービス
 WCF サービスは、サービスとクライアント間のコントラクトを定義するインターフェイスに基づいています。 マークされている、<xref:System.ServiceModel.ServiceContractAttribute>属性は、次のコードに示すようにします。

 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

 関数またはとしてマークすることによって、WCF サービスによって公開されているメソッドを定義する、<xref:System.ServiceModel.OperationContractAttribute>属性。 さらに、シリアル化されたデータを公開を持つ複合型をマークすることによって、<xref:System.Runtime.Serialization.DataContractAttribute>属性。 これにより、クライアントでのデータ バインディングできます。

 インターフェイスとそのメソッドを定義した後は、インターフェイスを実装するクラスでカプセル化します。 1 つの WCF サービス クラスには、複数のサービス コントラクトを実装できます。

 どのような使用量と呼ばれるに WCF サービスが公開される、*エンドポイント*します。 エンドポイントは、サービスと通信する唯一の方法を提供します。他のクラスと同様に、直接の参照を使用してサービスにアクセスすることはできません。

 エンドポイントは、アドレス、バインディング、およびコントラクトで構成されます。 アドレスの定義、サービスが存在します。URL、FTP アドレス、またはネットワークまたはローカル パスを指定できます。 バインディングは、サービスと通信する方法を定義します。 WCF バインドは、HTTP、FTP など、Windows 認証またはユーザー名とパスワード、セキュリティ メカニズムなどのプロトコルを指定するため汎用的なモデルを提供し、さらに多くします。 コントラクトには、WCF サービス クラスによって公開されている操作が含まれます。

 1 つの WCF サービスの複数のエンドポイントを公開することができます。 これには、さまざまな方法で、同じサービスと通信するさまざまなクライアントが使用できます。 たとえば、銀行のサービスは、1 つのエンドポイントの従業員と別のお客様に提供する外部、別のアドレス、バインディングを使用して各や、コントラクトします。

### <a name="wcf-client"></a>WCF クライアント
 WCF クライアントから成る、*プロキシ*WCF サービスと通信するアプリケーションを有効にして、サービスのエンドポイントに一致するエンドポイントが定義されています。 クライアント側でプロキシを生成、 *app.config*ファイルを開き、サービスによって公開されているメソッドや型に関する情報が含まれています。 複数のエンドポイントを公開するサービス、クライアントは HTTP 経由で通信し、Windows 認証を使用して、そのニーズに最適な 1 つを選択できます。

 WCF クライアントが作成された後は、他のオブジェクトと同様に、コード内でサービスを参照します。 たとえばを呼び出す、`GetData`メソッドは、次のようなコードを記述する前に示した。

 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio での WCF ツール
 Visual Studio には、WCF サービスと WCF クライアントの両方を作成するためのツールが用意されています。 ツールについて説明するチュートリアルでは、次を参照してください。[チュートリアル: Windows フォームにおける単純な WCF サービスを作成する](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)します。

### <a name="create-and-test-wcf-services"></a>作成し、WCF サービスのテスト
 WCF Visual Studio テンプレートは、独自のサービスをすばやく作成するのに基礎として使用できます。 デバッグし、テスト サービスを WCF サービスの自動ホストと WCF テスト クライアントを使用できます。 これらのツール、高速で簡単なデバッグとテストのサイクルを提供し、早い段階でホスティング モデルにコミットする必要があります。

#### <a name="wcf-templates"></a>WCF テンプレート
 WCF Visual Studio テンプレートでは、サービスの開発の基本クラスの構造を提供します。 いくつかの WCF テンプレートは、**新しいプロジェクトの追加** ダイアログ ボックス。 WCF サービス lLibrary プロジェクト、WCF サービスの web サイト、および WCF サービス項目テンプレートが含まれます。

 テンプレートを選択すると、サービス コントラクト、サービス実装、およびサービス構成ファイルが追加されます。 必要なすべての属性が既に追加、サービスの単純な"Hello World"型を作成して、コードを記述するがありませんでした。 関数と実際のサービスのメソッドを提供するコードを追加することは、もちろんが、テンプレートは、基本的な基盤を提供します。

 WCF テンプレートの詳細については、次を参照してください。 [WCF Visual Studio テンプレート](/dotnet/framework/wcf/wcf-vs-templates)します。

#### <a name="wcf-service-host"></a>WCF サービス ホスト
 Visual Studio デバッガーを起動すると (キーを押して**F5**) WCF サービス プロジェクトでは、WCF サービス ホスト ツールは自動的にサービスをローカルにホストを起動します。 WCF サービス ホストは、WCF サービス プロジェクト内のサービスを列挙、プロジェクトの構成をロードおよび、検出された各サービスのホストをインスタンス化します。

 WCF サービス ホストを使用すると、余分なコードを記述したり開発時に特定のホストにコミットすることがなく、WCF サービスをテストできます。

 WCF サービス ホストの詳細については、次を参照してください。 [WCF サービス ホスト (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)します。

#### <a name="wcf-test-client"></a>WCF テスト クライアント
 WCF テスト クライアント ツールでは、テスト パラメーターを入力し、その WCF サービスに入力することができ、サービスが返送する応答を表示します。 WCF サービス ホストと組み合わせて使用すると、テストできる便利なサービスを提供します。 ツールには、検索、 *%programfiles (x86) %\Microsoft Visual studio \2017\enterprise\common7\ide*フォルダー。

 キーを押すと**F5** WCF サービス プロジェクトをデバッグする WCF テスト クライアントが開き、構成ファイルで定義されているサービス エンドポイントの一覧を表示します。 パラメーターをテスト サービスを開始し、継続的にテストして、サービスを検証するには、このプロセスを繰り返します。

 WCF テスト クライアントの詳細については、次を参照してください。 [WCF テスト クライアント (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)します。

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio での WCF サービスへのアクセス
 Visual Studio がプロキシとサービスを使用して、追加のエンドポイントを自動的に生成する、WCF クライアントを作成するタスクを簡略化、**サービス参照の追加** ダイアログ ボックス。 すべての必要な構成情報に追加されます、 *app.config*ファイル。 ほとんど、時間のそれを使用するためにサービスをインスタンス行う必要があることができます。

 **サービス参照の追加** ダイアログ ボックスを使用するサービスのアドレスを入力したり、ソリューションで定義されているサービスを検索できます。 ダイアログ ボックスでは、サービスとそれらのサービスによって提供される操作の一覧を返します。 また、コード内でサービスを参照する、名前空間を定義することもできます。

 **サービス参照の構成** ダイアログ ボックスでは、サービスの構成をカスタマイズすることができます。 サービスのアドレスを変更、アクセス レベル、非同期動作、およびメッセージ コントラクト型を指定、および型の再利用を構成することができます。

## <a name="how-to-select-a-service-endpoint"></a>方法: サービス エンドポイントを選択します。
一部の Windows Communication Foundation (WCF) サービスでは、サービスと通信がクライアントにより複数のエンドポイントを公開します。 たとえば、サービスでは、1 つのエンドポイントの HTTP バインドとユーザー名とパスワードのセキュリティを使用して、FTP と Windows 認証を使用する 2 番目のエンドポイントを公開可能性があります。 最初のエンドポイントは、2 つ目は、イントラネットで使用可能性がありますが、ファイアウォールの外側からサービスにアクセスするアプリケーションで使用可能性があります。

このような場合は、指定することができます、`endpointConfigurationName`サービス参照のコンス トラクターのパラメーターとして。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>サービス エンドポイントを選択するには

1.  プロジェクト ノードを右クリックして WCF サービスへの参照を追加**ソリューション エクスプ ローラー**を選択して**サービス参照の追加**します。

2.  コード エディターでは、サービス参照のコンス トラクターを追加します。

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    >  置換*ServiceReference*サービス参照と置換の名前空間を持つ*Service1Client*サービスの名前に置き換えます。

3.  IntelliSense の一覧では、コンス トラクターのオーバー ロードを含むが表示されます。 選択、`endpointConfigurationName As String`オーバー ロードします。

4.  次のオーバー ロードは、次のように入力します。 `=` *ConfigurationName*ここで、 *ConfigurationName*を使用するエンドポイントの名前を指定します。

    > [!NOTE]
    >  使用可能なエンドポイントの名前がわからない場合は、それらを検索、 *app.config*ファイル。

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF サービスの使用可能なエンドポイントが見つかりません

1.  **ソリューション エクスプ ローラー**を右クリックし、 **app.config**サービス参照を含むプロジェクトのファイルをクリックして**オープン**します。 ファイルでは、コード エディターで表示されます。

2.  検索、`<Client>`ファイル内のタグ。

3.  下に検索、`<Client>`で始まるタグのタグ`<Endpoint>`します。

     サービス参照は、複数のエンドポイントを提供する場合があります複数`<Endpoint`タグ。

4.  内で、`<EndPoint>`タグが表示されます、 `name="` *SomeService* `"`パラメーター (場所*SomeService*エンドポイント名を表します)。 渡すことができるエンドポイントの名前が、`endpointConfigurationName As String`サービス参照のコンス トラクターのオーバー ロードします。

## <a name="how-to-call-a-service-method-asynchronously"></a>方法: 非同期サービス メソッドを呼び出す
Windows Communication Foundation (WCF) サービスのほとんどのメソッドは、同期または非同期で呼び出すことができます。 メソッドを非同期的に呼び出すには、低速接続で実行しているときに、メソッドが呼び出されるときに作業を続行するアプリケーションができるようにします。

既定では、サービスの参照がプロジェクトに追加されたときに同期的にメソッドを呼び出す構成されます。 設定を変更する非同期メソッドを呼び出す動作を変更することができます、**サービス参照の構成** ダイアログ ボックス。

> [!NOTE]
>  このオプションは、サービスごとに設定されます。 サービスのメソッドの 1 つは非同期的に呼び出されると、すべてのメソッドを非同期的に呼び出す必要があります。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>サービス メソッドを非同期的に呼び出す

1.  **ソリューション エクスプ ローラー**、サービス参照 を選択します。

2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**します。

3.  **サービス参照の構成**ダイアログ ボックスで、**非同期操作を生成する**チェック ボックスをオンします。

## <a name="how-to-bind-data-returned-by-a-service"></a>方法: サービスによって返されるデータのバインド
他のデータ ソースをコントロールにバインドすると同様、コントロールに Windows Communication Foundation (WCF) サービスによって返されるデータをバインドすることができます。 自動的に追加されますが、サービスにデータを返す複合型が含まれている場合に、WCF サービスへの参照を追加すると、**データソース**ウィンドウ。

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WCF サービスによって返された 1 つのデータ フィールドにコントロールをバインドするには

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。 **データソース**ウィンドウが表示されます。

2.  **データソース**ウィンドウで、サービス参照のノードを展開します。 サービスの表示によって返される任意の複合型。

3.  型のノードを展開します。 その型のデータ フィールドが表示されます。

4.  フィールドを選択し、データ型で利用可能なコントロールの一覧を表示するドロップダウン矢印をクリックします。

5.  バインドするコントロールの種類をクリックします。

6.  フィールドをフォームにドラッグします。 と共にをフォームにコントロールを追加、<xref:System.Windows.Forms.BindingSource>コンポーネントと<xref:System.Windows.Forms.BindingNavigator>コンポーネント。

7.  他のフィールドを手順 4 にバインドします。

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF サービスから返された複合型にコントロールをバインドするには

1.  **データ**メニューの  **データ ソースの**します。 **データソース**ウィンドウが表示されます。

2.  **データソース**ウィンドウで、サービス参照のノードを展開します。 サービスの表示によって返される任意の複合型。

3.  型のノードを選択し、使用可能なオプションの一覧を表示するドロップダウン矢印をクリックします。

4.  いずれかをクリックします**DataGridView**をグリッドにデータを表示するか、**詳細**個々 のコントロールにデータを表示します。

5.  ノードをフォームにドラッグします。 と共に、フォームに、コントロールを追加、<xref:System.Windows.Forms.BindingSource>コンポーネントと<xref:System.Windows.Forms.BindingNavigator>コンポーネント。

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>方法: 既存の型を再利用のサービスを構成します。
サービス参照がプロジェクトに追加されると、サービスで定義された任意の型は、ローカル プロジェクトで生成されます。 多くの場合、重複する型と作成、サービスを使用して一般的な[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型または型が共有ライブラリで定義されている場合。

この問題を避けるためには、参照先アセンブリの型は既定で共有されます。 型の 1 つまたは複数のアセンブリの共有を無効にする場合は、行うことができますよう、**サービス参照の構成** ダイアログ ボックス。

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>1 つのアセンブリで型の共有を無効にするには

1.  **ソリューション エクスプ ローラー**、サービス参照 を選択します。

2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**します。

3.  **サービス参照の構成**ダイアログ ボックスで、**参照されたアセンブリを指定した型を再利用**します。

4.  型の共有を有効にする各アセンブリのチェック ボックスを選択します。 型のアセンブリの共有を無効にするには、 チェック ボックスをオフのままにします。

### <a name="to-disable-type-sharing-in-all-assemblies"></a>すべてのアセンブリで型の共有を無効にするには

1.  **ソリューション エクスプ ローラー**、サービス参照 を選択します。

2.  **プロジェクト** メニューのをクリックして**サービス参照の構成**します。

3.  **サービス参照の構成** ダイアログ ボックスで、クリア、**参照されたアセンブリで型を再利用**チェック ボックスをオンします。

## <a name="related-topics"></a>関連トピック

| タイトル | 説明 |
| - | - |
| [チュートリアル : Windows フォームでの簡単な WCF サービスの作成](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Visual Studio で作成および WCF サービスのステップ バイ ステップ デモを提供します。 |
| [チュートリアル: WPF と Entity Framework を使用する WCF data service の作成](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | 作成して使用する方法の詳細なデモンストレーションを行います[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Visual Studio でします。 |
| [WCF 開発ツールの使用](/dotnet/framework/wcf/using-the-wcf-development-tools) | 作成し、Visual Studio で WCF サービスをテストする方法について説明します。 |
| | [方法: 追加、更新、または WCF データ サービス参照の削除](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md) | サービス参照とその回避方法で発生することがいくつかの一般的なエラーを表示します。 |
| [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md) | 一般的な問題のデバッグと WCF サービスのデバッグ時に発生する手法について説明します。 |
| [チュートリアル: n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | 型指定されたデータセットを作成し、TableAdapter とデータセット コードを複数のプロジェクトに分離する手順について説明します。 |
| [サービス参照 ダイアログ ボックスを構成します。](../data-tools/configure-service-reference-dialog-box.md) | ユーザー インターフェイス要素について説明します、**サービス参照の構成** ダイアログ ボックス。 |

## <a name="reference"></a>参照

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)