---
title: "Visual Studio 機能拡張アーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio、環境モデル"
  - "環境モデル、Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Visual Studio 機能拡張アーキテクチャ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境では \(IDE\)VSPackage をホストすると共有サービスを交換しやすくするためのフレームワークです。  次の例はIDE がユーザー インターフェイスを実装 \(UI\) します。  IDE はコンテナーのウィンドウと既定のツール バーおよびメニュー提供します。  またUI のプログラミングできる豊富な COM のインフラストラクチャを提供します。  設定を処理しルーティングする完全なコマンドは既存のインストールおよびコマンド セットへの簡単なアクセスを提供する開いているフレームワークが付与されます。  
  
## 拡張のアーキテクチャ  
 次の図は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 機能拡張のアーキテクチャを示します。  ソフトウェア アプリケーションの概念がないことに注意してください。  代わりにVSPackage というアプリケーションの機能を提供するソフトウェア コンポーネントをホストします。  この機能はサービスとして IDE で共有されます。  VSPackage ではサービスはVSPackage などのそのほかの使用。  標準 IDE はIDE のウィンドウ操作機能にアクセスするためのそのほかの範囲を<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> などの提供します。  
  
 ![環境アーキテクチャ グラフィック](../extensibility/internals/media/environment.png "environment")  
Visual Studio の汎用ビュー アーキテクチャ  
  
 VSPackage とサービス間のリレーションシップを双方向であることを確認します。  VSPackage で使用できるサービスを提供しましたが他 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> インターフェイスを使用して独自のサービスを提供できます。  このサービス ベースのアーキテクチャはサービスに関連するタスクを実行するインターフェイスのグループである Microsoft ActiveX デザイナーの実装から育ちました。  厳密な COM の視点から特定のサービスのすべてのインターフェイスは単一の COM クラスに実装する必要があります。  
  
 標準の IDE はVSPackage で使用される重要なサービスを <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>およびなどの <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell><xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 提供します。  次の表はこれらのサービスの一覧とその説明です。  詳細については、「[使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)」を参照してください。  
  
|IDE のサービス|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|基本的な機能VSPackageレジストリを処理する IDE のサービスへのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|ツール ウィンドウとドキュメント ウィンドウを作成する機能などIDE の基本的なウィンドウ操作と UI 関連の機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|プロジェクトを新しいプロジェクトを作成するために列挙できるなど基本的なソリューションに関連付けられた機能を提供しモニターのプロジェクトが変更されます。|  
  
 共有サービスのやり取りによってな統合については[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE と VSPackage は相互に依存します。  ただし近い相互作用にかかわらず異なる必要があります。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE では次のタスクを行います :  
  
-   外部 VSPackage で使用する重要なサービスを提供します。  
  
-   標準の UI 要素とへの参加を有効にするプログラミング可能なインターフェイスを提供します。  
  
-   VSPackage のインスタンスをユーザー アクションを確認するにはがサービスを要求する他の VSPackages に作成します。  
  
-   これを VSPackage 間の通信およびを調整できるようにするサービスを提供します。  
  
-   管理のソリューションと必要なファイル。  
  
-   ウィンドウ管理の指定。  
  
-   メニューツール バーおよびコンテキスト メニューなどのコマンド ルーティングとコマンド バーを提供します。  
  
-   プロパティの選択コンテキストおよび通貨。  
  
 VSPackage では次のタスクを行います :  
  
-   特定の初期化と終了ルーチンを実行する。  
  
-   適切なタイミングで適切な VSPackage の読み込みに IDE を使用してレジストリに書き込みますします。  
  
-   他の VSPackages との通信に必要なサービスが用意されています。  
  
-   新しいプロジェクトの種類エディターおよびデザイナーを実装します。  
  
-   拡張機能をタスク項目ツールボックス項目やオプション\] ダイアログ ボックスなどの組み込み UI 要素について説明します。  
  
## 参照  
 [Visual Studio Shell](../extensibility/internals/visual-studio-shell.md)   
 [Vspackages にあります。](../extensibility/internals/vspackages.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)