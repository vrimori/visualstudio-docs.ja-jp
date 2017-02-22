---
title: "展開を管理するためのプロジェクトの構成 | Microsoft Docs"
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
  - "プロジェクトの構成、展開を管理します。"
  - "プロジェクト [Visual Studio SDK] の展開を管理するための構成"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 展開を管理するためのプロジェクトの構成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

配置が物理的にビルド処理からデバッグおよびインストールのための予想される場所への出力項目を移動する操作になります。  たとえばWeb アプリケーションがローカル コンピューターでビルドした後にサーバーに配置される可能性があります。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトを配置するには2 とおりの方法をサポートします :  
  
-   配置プロセスの件名を指定します。  
  
-   配置プロセスのマネージャーとします。  
  
 ソリューションを配置する前に配置オプションを設定する配置プロジェクトを追加する必要があります。  配置プロジェクトが存在しない場合はENT2ENT \[入力\] メニューの \[ENT0ENT\] を選択するかソリューションを右クリックすると 1 を作成する場合はか。  \[入力\] ENT0ENT をクリックする  **リモート配置ウィザード**  選択したプロジェクトの ENT2ENT \[出力\] ダイアログ ボックスを開きます。  
  
 使用するリモート ウィザードを要求します \(Windows\)または Web プロジェクト出力グループに追加しファイルに配置するリモート コンピューターはアプリケーションの種類を含む配置します。  ウィザードの最後のページで選択したオプションの概要が表示されます。  
  
 別の環境に移動する必要がある配置プロセスにより出力アイテムの件名なプロジェクト。  これらの出力項目はプロジェクト出力をグループ化を許可する主な目的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> インターフェイスのパラメーターとして記述されています。  `IVsProjectCfg2` の実装に関する詳細については[出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md) を参照してください。  
  
 配置プロセスを管理する配置プロジェクトはコマンドを選択すると配置のコマンドを有効にし応答します。  配置プロジェクトを配置を<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>実行するにはインターフェイスを実装し呼び出しを報告するためのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>にするには状態イベントを展開します。  
  
 構成はビルドまたは配置の動作に影響する依存関係を指定できます。  依存関係を独自の構成がビルドまたは配置される前と後にビルドまたは配置する必要のあるプロジェクト ビルドまたは配置します。  プロジェクトのビルド依存関係が <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> のインターフェイスで記述され<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> インターフェイスとの依存関係を展開します。  詳細については、「[構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)」を参照してください。  
  
## 参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)