---
title: "ソース コントロールの VSPackage アーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理パッケージのアーキテクチャ"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# ソース コントロールの VSPackage アーキテクチャ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージは IDE が提供するサービスを使用する VSPackage です。  代わりにソース管理パッケージはソース管理の機能をサービスとして提供します。  またソース管理パッケージは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] への統合のソース管理のソース管理プラグインより多機能な方法です。  
  
 ソース管理プラグイン API を実装するソース管理プラグインは厳密なコントラクトによってです。  たとえばプラグインは既定の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のユーザー インターフェイスを置き換えることは \(UI\) できません。  またソース管理プラグイン API は独自のソース管理のモデルの実装をプラグインができません。  ただしソース管理パッケージは両方の制限を回避します。  ソース管理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージはユーザーのソース管理機能を完全に制御します。  またパッケージにはソース管理のソース管理のモデルとロジックを使用するすべてのソース コントロールに関連するユーザー インターフェイスを定義できます。  
  
## ソース管理パッケージ コンポーネント  
 アーキテクチャ図に示すように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコンポーネントはソース管理のスタブが [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージのソース管理を統合する VSPackage としました。  
  
 ソース管理のスタブは次のタスクを行います。  
  
-   共通の UI を提供するパッケージ ソース管理の登録に必要です。  
  
-   ソース管理パッケージを読み込みます。  
  
-   アクティブまたは非アクティブとしてソース管理パッケージを設定します。  
  
 ソース管理のスタブがソース管理パッケージのアクティブなサービスを検索しIDE でそのパッケージに入力されたすべての呼び出しを転送します。  
  
 ソース管理のアダプターのパッケージは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が提供する特別なソース管理パッケージです。  このパッケージはソース管理プラグイン API に基づいてソース管理プラグインをサポートするための中核となるコンポーネントです。  ソース管理プラグインがアクティブなプラグインの場合ソース管理のスタブがソース管理のアダプターのパッケージにイベントを送信します。  次にソース管理のアダプターのパッケージはソース管理プラグインとすべてのソース管理のプラグインに共通のソース管理プラグイン API を使用して通信します。また既定の UI を提供します。  
  
 ソース管理パッケージがアクティブなパッケージの一方とソース管理のスタブがパッケージと [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] パッケージのソース管理インターフェイスを使用して直接通信します。  パッケージにはソース管理のソース管理の UI をホストするために使用します。  
  
 ![ソース管理アーキテクチャ グラフィック](~/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 ソース管理のパッケージは[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は統合のソース・コード管理や API を提供しません。  ソース管理プラグインが短い一連のコールバックおよびコールバック関数を実装する必要がある [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md) に記載されている方法と比較してみてください。  
  
 VSPackageのようにソース管理 `CoCreateInstance` パッケージはを使用して作成できる COM オブジェクトです。  VSPackage では自身を <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> を実行して [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE で使用できるようにします。  インスタンスが作成されるとVSPackageサイトのポインターを IDE の使用できるサービスとインターフェイスに VSPackage のアクセスを提供する <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> のインターフェイスを受け取ります。  
  
 VSPackage ベースのソース管理パッケージを記述することが必要です。ソース管理にプラグイン API ベースのプラグインを作成しより高度なプログラミングの知識を示します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [作業の開始](../../extensibility/internals/getting-started-with-source-control-vspackages.md)