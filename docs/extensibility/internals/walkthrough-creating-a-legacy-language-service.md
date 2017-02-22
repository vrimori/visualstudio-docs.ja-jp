---
title: "チュートリアル: 従来の言語サービスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成する言語サービス [マネージ パッケージ framework]"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# チュートリアル: 従来の言語サービスの作成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

マネージ パッケージ フレームワーク \(MPF\) 言語のクラスを使用して、言語サービスを実装する [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] は簡単です。 言語サービス、言語サービス自体、および言語のパーサーをホストする VSPackage が必要です。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## Visual Studio パッケージのプロジェクト テンプレートの場所  
 次の 3 つの異なるテンプレートの場所で、Visual Studio パッケージ プロジェクト テンプレートが見つかりません、 **新しいプロジェクト** \] ダイアログ ボックス。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C\# の機能拡張の下。 プロジェクトの既定の言語は C\# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C\+\+ です。  
  
### VSPackage を作成します。  
  
1.  Visual Studio パッケージ プロジェクト テンプレートを使用して新しい VSPackage を作成します。  
  
     言語サービスを既存の vs パッケージに追加する場合は、次の手順をスキップし、「言語サービス クラスを作成する」の手順に直接移動します。  
  
2.  MyLanguagePackage をプロジェクトの名前を入力し、クリックして **OK**します。  
  
     必要な任意の名前を使用することができます。 ここで詳しく説明するこれらの手順では、名前として MyLanguagePackage があるとします。  
  
3.  選択 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] と言語の新しいキー ファイルを生成するオプションです。**\[次へ\]** をクリックします。  
  
4.  適切な企業およびパッケージの情報を入力します。**\[次へ\]** をクリックします。  
  
5.  選択 **メニュー コマンド**します。**\[次へ\]** をクリックします。  
  
     コード スニペットをサポートする予定がない場合はだけ完了\] をクリックし、次の手順を無視します。  
  
6.  入力 **スニペットを挿入** として、 **コマンド名** と `cmdidInsertSnippet` の **コマンド ID**します。**\[完了\]** をクリックします。  
  
     **コマンド名** と **コマンド ID** 必要な値を指定できます、これらは単なる例です。  
  
### 言語サービス クラスを作成します。  
  
1.  **ソリューション エクスプ ローラー**, MyLanguagePackage プロジェクトを右クリックしてで、 **追加**, 、**参照**, を選択し、 **新しい参照の追加** \] ボタンをクリックします。  
  
2.  **参照の追加** ダイアログ ボックスで、 **Microsoft.VisualStudio.Package.LanguageService** で、 **.NET** \] タブでをクリックし、 **OK**します。  
  
     これは、言語のプロジェクトのパッケージに 1 回だけ実行する必要があります。  
  
3.  **ソリューション エクスプ ローラー**, VSPackage プロジェクトを右クリックして、選択 **追加**, 、**クラス**します。  
  
4.  確認 **クラス** がテンプレートの一覧で選択されています。  
  
5.  入力 **MyLanguageService.cs** のクラス ファイルをクリックして名前を **追加**します。  
  
     必要な任意の名前を使用することができます。 これらの手順をここで詳しく説明 `MyLanguageService` 名として。  
  
6.  MyLanguageService.cs ファイルに次のコードを追加 `using` ステートメントです。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  変更、 `MyLanguageService` クラスから派生する、 <xref:Microsoft.VisualStudio.Package.LanguageService> クラス。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  "LanguageService"上にカーソルを配置、 **編集**, 、**IntelliSense** メニューの \[ **抽象クラスの実装**します。 これは、言語サービス クラスを実装する場合は、最低限必要なメソッドを追加します。  
  
9. 抽象メソッドを実装する」の説明に従って [言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)します。  
  
### 言語サービスを登録します。  
  
1.  MyLanguagePackagePackage.cs ファイルを開き、次の追加 `using` ステートメント。  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  」の説明に従って、言語サービス クラスを登録 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)します。 これには、ProvideXX 属性と「、言語サービス Proffering」セクションが含まれます。 このトピックが TestLanguageService を使用して MyLanguageService を使用します。  
  
### パーサーとスキャナー  
  
1.  説明するように、パーサーと、対象の言語のスキャナーを実装 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。  
  
     パーサーとスキャナーを実装する方法と、すべて開発者はあり、このトピックの範囲を超えてです。  
  
## 言語サービスの機能  
 言語サービスでは、各機能を実装するに通常適切な MPF 言語サービス クラスから派生クラスを作成、必要に応じて、抽象メソッドを実装および適切なメソッドをオーバーライドします。 作成したりから派生するクラスは、機能依存をサポートする予定があります。 これらの機能の詳細に説明されている [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)します。 次の手順は、MPF クラスからクラスを派生する一般的なアプローチです。  
  
#### MPF クラスから派生します。  
  
1.  **ソリューション エクスプ ローラー**, VSPackage プロジェクトを右クリックして、選択 **追加**, 、**クラス**します。  
  
2.  確認 **クラス** がテンプレートの一覧で選択されています。  
  
     クラス ファイルの適切な名前を入力し、クリックして **追加**します。  
  
3.  新しいクラス ファイルで次のコードを追加 `using` ステートメントです。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  目的の MPF クラスから派生するクラスを変更します。  
  
5.  基本クラスのコンス トラクターと同じパラメーターを受け取るには、少なくともクラスのコンス トラクターを追加し、基本クラス コンス トラクターにコンス トラクターのパラメーターを渡します。  
  
     たとえばから派生したクラスのコンス トラクター、 <xref:Microsoft.VisualStudio.Package.Source> クラスは、次のようになります。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  **編集**, 、**IntelliSense** メニューの \[ **抽象クラスの実装** 場合は、基底クラスがある、抽象メソッドを実装する必要があります。  
  
7.  それ以外の場合、クラスの内側にキャレットを配置し、オーバーライドするメソッドを入力します。  
  
     たとえば、「 `public override` そのクラスでオーバーライド可能なすべてメソッド一覧を表示します。  
  
## 参照  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)