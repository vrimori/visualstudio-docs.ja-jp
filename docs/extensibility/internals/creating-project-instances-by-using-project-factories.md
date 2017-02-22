---
title: "プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。 | Microsoft Docs"
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
  - "プロジェクトのファクトリ"
  - "プロジェクト [Visual Studio SDK] プロジェクト ファクトリ"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の種類のプロジェクトではプロジェクトのオブジェクトのインスタンスを作成するには *プロジェクト ファクトリを*  使用します。  プロジェクト ファクトリは cocreatable COM オブジェクトの標準クラス ファクトリに似ています。  ただしプロジェクトのオブジェクトは cocreatable ではありません : 項目はプロジェクト ファクトリを使用してしか作成できません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE はユーザーが既存のプロジェクトを読み込むか[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で新しいプロジェクトを作成するときにプロジェクト ファクトリを VSPackage で実行されて呼び出されます。  新しいプロジェクトのオブジェクトは設定のソリューション エクスプローラーに十分な情報を IDE にあります。  新しいプロジェクトのオブジェクトにはIDE による関連するすべての UI 操作をサポートするように要求インターフェイスを提供します。  
  
 プロジェクトのクラスの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> のインターフェイスを実装できます。  通常は独自のモジュールに存在します。  
  
 `IVsProjectFactory` のインターフェイスの実装の例については[Basic Project](http://msdn.microsoft.com/ja-jp/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) サンプル ディレクトリに含まれる PrjFac.cpp を参照してください。  
  
 所有者によって集約をサポートするプロジェクトではプロジェクト ファイルに保持する必要があります。キーの所有者  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> のメソッドがオーナーのキーでプロジェクトの場合所有するプロジェクトはプロジェクト ファクトリの GUID を所有者のキーを変換し実際のを作成するにはこのプロジェクト ファクトリの `CreateProject` のメソッドを呼び出します。  
  
## 所有されたプロジェクトの作成  
 所有者は 2 段階の所有されたプロジェクトを作成します :  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> メソッドを呼び出します。  これは所有するプロジェクトに `IUnknown` を制御する入力に基づいて集約されたプロジェクトのオブジェクトを作成する可能性があります。  所有するプロジェクトはプロジェクトの所有者に対して内部の `IUnknown` と集約オブジェクトを渡します。  これは所有されたプロジェクト内の `IUnknown` を格納する可能性があります。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> メソッドを呼び出します。  所有するプロジェクトは所有されていないプロジェクトの場合を実行する場合はこのメソッドが `IVsProjectFactory::CreateProject` の代わりに入っているすべてをインスタンス化します。  入力 `VSOWNEDPROJECTOBJECT` の列挙型は通常集計所有されているプロジェクトです。  所有するプロジェクトはクッキーが null 値ではありません\) プロジェクトのオブジェクトが既に作成されているかどうかを確認するにはこの変数を使用することを作成する必要があります \(クッキー\) からの null 値\)。  
  
 プロジェクトの種類は cocreatable COM オブジェクトの CLSID と同様に一意のプロジェクトの GUID で識別されます。  通常 1 プロジェクト ファクトリのハンドルを持つことができる複数のプロジェクトの GUID ですが一つのプロジェクトでの型のインスタンスを作成する 1 種類のプロジェクト ファクトリのハンドル。  
  
 プロジェクトの種類は特定のファイル名拡張子に関連付けられます。  ユーザーが既存のプロジェクト ファイルを開こうとしたかテンプレートを複製することで新しいプロジェクトを作成しようとするとIDE では対応するプロジェクトの GUID を確認するにはファイルの拡張子を使用します。  
  
 新しいプロジェクトを作成するか特定の型の既存のプロジェクトを開く IDE があるかどうかを決定したら IDE にはVSPackage が必要なプロジェクト ファクトリを実装するシステム レジストリの検索の情報を \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ Projects\] を使用します。  IDE ではこの VSPackage を読み込みます。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> のメソッドではVSPackage は <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> のメソッドを呼び出してIDE のプロジェクト ファクトリを登録する必要があります。  
  
 `IVsProjectFactory` インターフェイスの基本的な方法は 2 種類のシナリオを処理するか <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> です : 新しいプロジェクトと既存のプロジェクトを開きます。  ほとんどのプロジェクトではプロジェクト ファイルでプロジェクトの状態を保存します。  通常は新しいプロジェクトはコピーを `CreateProject` のメソッドに渡されるテンプレート ファイルの作成コピーを開くことによって作成されます。  既存のプロジェクトを直接 `CreateProject` のメソッドに渡されるプロジェクト ファイルを開くことによってインスタンス化されます。  `CreateProject` のメソッドは必要に応じてユーザーの UI の機能を表示できます。  
  
 代わりにプロジェクトはデータベースまたは Web サーバーなどファイル システム以外のストレージ機構でプロジェクトの状態を格納するためにあるファイルを使用します。  この場合`CreateProject` のメソッドに渡されたファイル名パラメーターは実際にファイル システム パスではありませんが一意の文字列はURL にプロジェクトのデータを識別します。  実行する適切なコンストラクターのシーケンスを生成するに `CreateProject` に渡されるテンプレート ファイルをコピーする必要はありません。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)