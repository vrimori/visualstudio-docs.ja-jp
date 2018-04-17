---
title: 'チュートリアル: 従来の言語サービスの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb1fc7b6c35b2ee6ef3a767f7093f2fa0e4cb972
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>チュートリアル: 従来の言語サービスの作成
マネージ パッケージ フレームワーク (MPF) 言語のクラスを使用して、言語のサービスを実装する[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]は簡単です。 VSPackage、言語サービス、言語サービス自体、および言語パーサーをホストする必要があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../../extensibility/visual-studio-sdk.md)です。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージのプロジェクト テンプレートの場所  
 次の 3 つの異なるテンプレートの場所で、Visual Studio パッケージ プロジェクト テンプレートが見つかりません、**新しいプロジェクト** ダイアログ ボックス。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C# の機能拡張の下。 プロジェクトの既定の言語は C# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C++ です。  
  
### <a name="create-a-vspackage"></a>VSPackage を作成します。  
  
1.  Visual Studio パッケージ プロジェクト テンプレートを使って新しい VSPackage を作成します。  
  
     既存の VSPackage に言語サービスを追加する場合、次の手順をスキップし、「言語サービス クラスを作成する」の手順に直接移動します。  
  
2.  MyLanguagePackage をプロジェクトの名前を入力し、クリックして**OK**です。  
  
     必要な任意の名前を使用することができます。 ここで詳細な手順では、名前として MyLanguagePackage と仮定します。  
  
3.  選択[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]言語と、新しいキー ファイルを生成するオプションとして。 **[次へ]**をクリックします。  
  
4.  適切な会社とパッケージの情報を入力します。 **[次へ]**をクリックします。  
  
5.  選択**メニュー コマンド**です。 **[次へ]**をクリックします。  
  
     コード スニペットをサポートする予定がない場合だけ完了 をクリックし、次の手順を無視します。  
  
6.  入力**スニペットを挿入**として、**コマンド名**と`cmdidInsertSnippet`の**コマンド ID**です。 **[完了]**をクリックします。  
  
     **コマンド名**と**コマンド ID**何でも使用できますが、これらは単なる例です。  
  
### <a name="create-the-language-service-class"></a>言語サービス クラスを作成します。  
  
1.  **ソリューション エクスプ ローラー**MyLanguagePackage プロジェクトを右クリックしてで、**追加**、**参照**を選択し、 **の新しい参照の追加**ボタンをクリックします。  
  
2.  **参照の追加**ダイアログ ボックスで、 **Microsoft.VisualStudio.Package.LanguageService**で、 **.NET**  タブでをクリックし、 **OK**です。  
  
     これは、言語パッケージのプロジェクトに 1 回だけ実行する必要があります。  
  
3.  **ソリューション エクスプ ローラー**、VSPackage プロジェクトを右クリックし、選択、**追加**、**クラス**です。  
  
4.  確認**クラス**がテンプレートの一覧で選択されています。  
  
5.  入力**MyLanguageService.cs**  をクリックして、クラス ファイルの名前の**追加**です。  
  
     必要な任意の名前を使用することができます。 これらの手順をここで詳しく説明`MyLanguageService`名として。  
  
6.  MyLanguageService.cs ファイルに次のコードを追加`using`ステートメントです。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  変更、`MyLanguageService`から派生するクラス、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  "LanguageService"上にカーソルを置き、**編集**、 **IntelliSense**メニューの **抽象クラスの実装**です。 これは、言語サービス クラスを実装する場合は、最低限必要なメソッドを追加します。  
  
9. 抽象メソッドを実装する」の説明に従って[レガシ言語サービスを実装する](../../extensibility/internals/implementing-a-legacy-language-service2.md)です。  
  
### <a name="register-the-language-service"></a>言語サービスを登録します。  
  
1.  MyLanguagePackagePackage.cs ファイルを開き、次の追加`using`ステートメント。  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  クラスを登録、言語サービス」の説明に従って[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)です。 これには、ProvideXX 属性と「、言語サービス Proffering」セクションが含まれます。 このトピックの内容が TestLanguageService をで使用されている MyLanguageService を使用します。  
  
### <a name="the-parser-and-scanner"></a>パーサーとスキャナー  
  
1.  パーサーと、言語のスキャナーを」の説明に従って実装[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)です。  
  
     パーサーとスキャナーを実装する方法と、完全に依存するはこのトピックの範囲外です。  
  
## <a name="language-service-features"></a>言語サービス機能  
 言語サービスで各機能を実装するに通常、適切な MPF 言語サービス クラスからクラスを派生、必要に応じて、抽象メソッドを実装して、適切なメソッドをオーバーライドします。 作成したりから派生するクラスは、機能依存をサポートする予定があります。 これらの機能の詳細については[レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)します。 次の手順は、MPF クラスからクラスを派生する一般的なアプローチです。  
  
#### <a name="deriving-from-an-mpf-class"></a>MPF クラスから派生します。  
  
1.  **ソリューション エクスプ ローラー**、VSPackage プロジェクトを右クリックし、選択、**追加**、**クラス**です。  
  
2.  確認**クラス**がテンプレートの一覧で選択されています。  
  
     クラス ファイルの適切な名前を入力し、クリックして**追加**です。  
  
3.  新しいクラス ファイルで次のコードを追加`using`ステートメントです。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  目的の MPF クラスから派生するクラスを変更します。  
  
5.  基本クラスのコンス トラクターと同じパラメーターを受け取るには、少なくともクラスのコンス トラクターを追加し、コンス トラクターのパラメーターを基底クラス コンス トラクターにログオンします。  
  
     たとえばから派生したクラスのコンス トラクター、<xref:Microsoft.VisualStudio.Package.Source>クラスは、次のようになります。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  **編集**、 **IntelliSense**メニューの **抽象クラスの実装**基底クラスに実装する必要がある抽象メソッドがある場合。  
  
7.  それ以外の場合、クラスの内側にキャレットを配置し、オーバーライドするメソッドを入力します。  
  
     たとえば、「`public override`そのクラスでオーバーライド可能なすべてメソッド一覧を表示します。  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)