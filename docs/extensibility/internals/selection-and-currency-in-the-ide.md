---
title: "選択と、IDE 内の通貨 | Microsoft Docs"
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
  - "Visual Studio IDE の通貨"
  - "IDE の選択"
  - "選択した場合、Visual Studio IDE"
  - "IDE、通貨"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 選択と、IDE 内の通貨
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) では、選択範囲を使用して、現在選択したオブジェクトに関するユーザーの情報は保持 *コンテキスト*します。 選択コンテキスト VSPackages は 2 つの方法で追跡の通貨で一部を実行できます。  
  
-   で、IDE に VSPackages に関する通貨情報を伝達します。  
  
-   IDE 内でユーザーの現在アクティブな選択項目を監視します。  
  
## 選択コンテキスト  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE グローバルの追跡固有のグローバルの選択コンテキスト オブジェクトで IDE 通貨です。 次の表は、選択コンテキストを構成する要素を示しています。  
  
|要素|説明|  
|--------|--------|  
|現在の階層|通常、現在のプロジェクトです。NULL の現在の階層では、ソリューション全体が現在のものを示します。|  
|現在のアイテム Id|現在の階層内で選択された項目選択した複数のプロジェクト\] ウィンドウで、あるときは、複数の現在の項目があります。|  
|現在 `SelectionContainer`|1 つまたは複数のオブジェクトのプロパティ\] ウィンドウがプロパティを表示する必要がありますが保持されます。|  
  
 さらに、環境では、2 つのグローバル リストを保持しています。  
  
-   アクティブな UI コマンド識別子の一覧  
  
-   現在アクティブな要素の型のリスト。  
  
### ウィンドウの種類と選択  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、2 つの一般的な種類に windows を整理します。  
  
-   階層型の windows  
  
-   ツールとドキュメント ウィンドウなどのフレーム ウィンドウ  
  
 IDE は、これらのウィンドウの種類ごとに異なる通貨を追跡します。  
  
 最も一般的なプロジェクトの種類\] ウィンドウは、IDE を制御する \[ソリューション エクスプ ローラーです。 プロジェクトの種類\] ウィンドウは、グローバルな階層とグローバルの選択コンテキストの ItemID を追跡し、ウィンドウは、現在の階層を決定する、ユーザーの選択に依存しています。 環境が、グローバル サービスを提供するプロジェクトの種類の windows 用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, 通じてどの VSPackages が開いている要素の現在の値を監視できます。 プロパティの参照、環境では、このグローバル サービスによって左右されます。  
  
 フレーム ウィンドウは、DocObject をフレーム ウィンドウ内で、SelectionContext 値 \(階層\/ItemID\/SelectionContainer とも\) をプッシュするのに一方で、使用します。 」を参照してください。 フレーム ウィンドウは、サービスを使用して <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> この目的のためです。 DocObject は選択コンテナーの値のみをプッシュできます階層のローカルの値はそのままおよび通常 MDI 子ドキュメントの ItemID がそのままです。  
  
### イベントと通貨  
 通貨の環境の概念に影響する 2 種類のイベントが発生する可能性があります。  
  
-   イベントには、グローバル レベルに伝達され、ウィンドウ フレームの選択コンテキストを変更します。 この種類のイベントの例には、開いているグローバル ツール ウィンドウまたは開いているプロジェクトの種類のツール ウィンドウは、開いている MDI 子ウィンドウが含まれます。  
  
-   トレース ウィンドウ フレームの選択コンテキスト内で要素を変更するイベントです。 例には、プロジェクトの種類\] ウィンドウで選択を変更するか DocObject 内の選択項目の変更が含まれます。  
  
## 参照  
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)   
 [ユーザーへのフィードバック](../../extensibility/internals/feedback-to-the-user.md)