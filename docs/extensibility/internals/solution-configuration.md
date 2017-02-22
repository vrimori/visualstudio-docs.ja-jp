---
title: "ソリューション構成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソリューションの構成"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ソリューション構成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソリューション構成には、ソリューション レベルのプロパティが保存されます。 動作を指示する、 **Start** \(F5\) キーと **Build** コマンドです。 既定では、これらのコマンドは、ビルドして、デバッグ構成を開始します。 どちらのコマンドは、ソリューション構成のコンテキストで実行します。 これは、ユーザーがどのようなアクティブなソリューションがの設定で構成されているビルドの開始、f5 キーを予測できることを意味します。 環境は、ビルドおよび実行する際に、プロジェクトではなく、ソリューションを最適化するために設計されています。  
  
 標準の Visual Studio ツールバーには、\[スタート\] ボタンとドロップダウンを \[スタート\] ボタンの右側に使用するソリューション構成が含まれています。 この一覧では、f5 キーが押されたときに開始する構成を選択して、独自のソリューション構成を作成または既存の構成を編集することができます。  
  
> [!NOTE]
>  機能拡張インターフェイスを作成またはソリューション構成を編集することはありません。 使用する必要があります `DTE.SolutionBuilder`します。 ただし、ソリューションのビルドを管理するのには機能拡張 Api があります。 詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>」を参照してください。  
  
 プロジェクトの種類でサポートされているソリューション構成を実装する方法を次に示します。  
  
-   プロジェクト  
  
     現在のソリューションに存在するプロジェクトの名前を表示します。  
  
-   構成  
  
     プロジェクトの種類でサポートされている構成の一覧を提供および実装プロパティ ページに表示する <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>です。  
  
     構成\] 列では、このソリューション構成でビルドするプロジェクト構成の名前を表示し、矢印ボタンをクリックするとすべてのプロジェクト構成の一覧を表示します。 環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> メソッドがこの一覧に入力します。 場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> メソッド示すことをサポートするプロジェクト構成の編集、新規または編集の選択は、\[構成\] の下も表示されます。 これらの各選択のメソッドを呼び出すためのダイアログ ボックスを起動、 `IVsCfgProvider2` プロジェクトの構成を編集するインターフェイスです。  
  
     プロジェクトが構成をサポートしていない場合、構成\] 列は \[なし\] が表示されは無効になります。  
  
-   プラットフォーム  
  
     選択したプロジェクトの構成に対して、ビルドし、矢印ボタンをクリックするとは、すべてのプロジェクトで使用可能なプラットフォームの一覧表示、プラットフォームが表示されます。 環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> メソッドがこの一覧に入力します。 場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> メソッド示すことをサポートするプロジェクトのプラットフォームを編集する新規または編集の選択内容はプラットフォームの見出しの下も表示されます。 これらの各選択を呼び出すためのダイアログ ボックスを起動 `IVsCfgProvider2` プロジェクトの使用可能なプラットフォームを編集します。  
  
     プロジェクトがプラットフォームをサポートしていない場合、そのプロジェクトのプラットフォームの列は \[なし\] が表示されは無効になります。  
  
-   ビルド  
  
     現在のソリューション構成でプロジェクトをビルドするかどうかを指定します。 ソリューション レベルのビルド コマンドが含まれているプロジェクトの依存関係にかかわらず呼び出されたときに、選択されていないプロジェクトはビルドされません。 指定されていないビルドするプロジェクトはまだデバッグ、実行中、パッケージ、およびソリューションの展開に含まれます。  
  
-   配置  
  
     選択したソリューションのビルド構成を使用開始」または「配備コマンドを使用する場合に、プロジェクトを配置するどうかを指定します。 このフィールドのチェック ボックスが使用できるは、プロジェクトは、実装することによって展開をサポートしている場合は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> インターフェイスをその <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> オブジェクトです。  
  
 新しいソリューション構成が追加されると、ユーザーを選択できますが、ソリューション構成ドロップダウン リスト ボックスから \[標準\] ツールバーを作成したり、その構成を開始したりします。  
  
## 参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)