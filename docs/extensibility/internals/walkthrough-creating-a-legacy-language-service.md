---
title: 'チュートリアル: 従来の言語サービスを作成する |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7aded5dcc3e3cf9e50485d50659c0400c045051d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001057"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>チュートリアル: 従来の言語サービスを作成します。
マネージ パッケージ フレームワーク (MPF) 言語のクラスを使用してでの言語サービスを実装する[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]は簡単です。 言語サービス、言語サービス自体には、お使いの言語のパーサーをホストするために VSPackage が必要です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../../extensibility/visual-studio-sdk.md)します。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージ プロジェクト テンプレートは次の 3 つの異なるテンプレートの場所で見つかる、**新しいプロジェクト** ダイアログ ボックス。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C# の機能拡張の下。 プロジェクトの既定の言語は C# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C++ です。  
  
### <a name="create-a-vspackage"></a>VSPackage を作成します。  
  
1. Visual Studio パッケージ プロジェクト テンプレートを使って新しい VSPackage を作成します。  
  
    既存の VSPackage に言語サービスを追加する場合は、次の手順をスキップして、「言語サービス クラスを作成する」手順に進みます。  
  
2. MyLanguagePackage をプロジェクトの名前を入力し、クリックして**OK**します。  
  
    任意の名前を使用することができます。 ここで説明するこれらの手順では、名前として MyLanguagePackage を想定しています。  
  
3. 選択[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と言語の新しいキー ファイルを生成するオプション。 **[次へ]** をクリックします。  
  
4. 適切なパッケージおよび会社の情報を入力します。 **[次へ]** をクリックします。  
  
5. 選択**メニュー コマンド**します。 **[次へ]** をクリックします。  
  
    コード スニペットをサポートする予定がない場合だけ完了 をクリックし、次の手順を無視します。  
  
6. 入力**スニペットを挿入**として、**コマンド名**と`cmdidInsertSnippet`の**コマンド ID**します。 **[完了]** をクリックします。  
  
    **コマンド名**と**コマンド ID**何でもできますが、これらは単なる例です。  
  
### <a name="create-the-language-service-class"></a>言語サービス クラスを作成します。  
  
1.  **ソリューション エクスプ ローラー**、MyLanguagePackage プロジェクトを右クリックし、選択**追加**、**参照**を選択し、 **の新しい参照の追加**ボタンをクリックします。  
  
2.  **参照の追加**ダイアログ ボックスで、 **Microsoft.VisualStudio.Package.LanguageService**で、 **.NET**  タブでをクリックし、 **OK**します。  
  
     これは、言語パッケージ プロジェクトでは 1 回だけ実行する必要があります。  
  
3.  **ソリューション エクスプ ローラー**VSPackage プロジェクトを右クリックし、選択、**追加**、**クラス**します。  
  
4.  必ず**クラス**がテンプレートの一覧で選択されています。  
  
5.  入力**MyLanguageService.cs**のクラス ファイルをクリックして名前**追加**します。  
  
     任意の名前を使用することができます。 これらの手順をここで説明する`MyLanguageService`名として。  
  
6.  MyLanguageService.cs ファイルで次の追加`using`ステートメント。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  変更、`MyLanguageService`クラスから派生する、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  "LanguageService"でとの間にカーソルを置き、**編集**、 **IntelliSense**メニューの **抽象クラスの実装**します。 これには、言語サービス クラスを実装するために必要な最低限の方法が追加されます。  
  
9. 抽象メソッドの実装」の説明に従って[従来の言語サービスを実装する](../../extensibility/internals/implementing-a-legacy-language-service2.md)します。  
  
### <a name="register-the-language-service"></a>言語サービスを登録します。  
  
1.  MyLanguagePackagePackage.cs ファイルを開き、次の追加`using`ステートメント。  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  言語サービス クラスを登録する」の説明に従って[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)します。 これは、「、言語サービス Proffering」のセクションでは、ProvideXX 属性が含まれます。 このトピックでは使用 TestLanguageService MyLanguageService を使用します。  
  
### <a name="the-parser-and-scanner"></a>パーサーとスキャナー  
  
1.  パーサーとスキャナーの言語の実装」の説明に従って[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。  
  
     パーサーとスキャナーを実装する方法を決めと、このトピックの範囲外です。  
  
## <a name="language-service-features"></a>言語サービスの機能  
 言語サービスで各機能を実装するために通常 MPF 言語サービスの適切なクラスからクラスを派生、必要に応じて、抽象メソッドを実装して適切なメソッドをオーバーライドします。 サポート対象を作成したりから派生するクラスは、機能に依存します。 これらの機能がで詳しく説明されている[レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)します。 次の手順は、MPF クラスからクラスを派生する一般的なアプローチです。  
  
#### <a name="deriving-from-an-mpf-class"></a>MPF クラスから派生します。  
  
1.  **ソリューション エクスプ ローラー**VSPackage プロジェクトを右クリックし、選択、**追加**、**クラス**します。  
  
2.  必ず**クラス**がテンプレートの一覧で選択されています。  
  
     クラス ファイルの適切な名前を入力し、クリックして**追加**します。  
  
3.  次の追加、新しいクラス ファイルで`using`ステートメント。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  目的の MPF クラスから派生するクラスを変更します。  
  
5.  基本クラスのコンス トラクターと同じパラメーターを受け取るには少なくともクラスのコンス トラクターを追加し、基本クラス コンス トラクターにコンス トラクターのパラメーターを渡します。  
  
     たとえばから派生したクラスのコンス トラクター、<xref:Microsoft.VisualStudio.Package.Source>クラスは、次のようになります。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  **編集**、 **IntelliSense**メニューの **抽象クラスの実装**基底クラスで実装する必要がある抽象メソッドがある場合。  
  
7.  それ以外の場合、クラスの内側にキャレットを配置し、メソッドのオーバーライドを入力します。  
  
     たとえば、「`public override`そのクラスでオーバーライド可能なすべてメソッド一覧を表示します。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの実装](../../extensibility/internals/implementing-a-legacy-language-service1.md)