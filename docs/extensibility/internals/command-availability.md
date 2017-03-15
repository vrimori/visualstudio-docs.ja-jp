---
title: "利用可能なコマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド、コンテキスト"
  - "メニュー項目、可視性コンテキスト"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# 利用可能なコマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio のコンテキストでは、どのコマンドは、使用を決定します。 コンテキストは、現在のプロジェクト、現在のエディター、読み込まれる Vspackage および統合開発環境 \(IDE\) の他の要素に応じて変更できます。  
  
## コマンドのコンテキスト  
 次のコマンドのコンテキストは、最も一般的です。  
  
-   **IDE** IDE で提供されるコマンドが常に表示します。  
  
-   **VSPackage** 表示または非表示にするコマンド処理される Vspackage を定義できます。  
  
-   **プロジェクト** プロジェクトのコマンドは、現在選択されているプロジェクトにのみ表示されます。  
  
-   **エディター** 、一度にアクティブにできるエディターの 1 つだけです。 アクティブなエディターからのコマンドを利用できます。 エディターは、言語サービスと密接に連携します。 言語サービスは、関連付けられたエディターのコンテキストでは、そのコマンドを処理する必要があります。  
  
-   **ファイルの種類** エディターは、1 つ以上の種類のファイルを読み込むことができます。 使用可能なコマンドは、ファイルの種類に応じて変更できます。  
  
-   **アクティブなウィンドウ** 最後の作業中のドキュメント ウィンドウは、ショートカット キーのユーザー インターフェイス \(UI\) のコンテキストを設定します。 ただし、内部の Web ブラウザーのようなキー バインド テーブルのあるツール ウィンドウでは、UI コンテキストが設定もできます。 HTML エディターなど、マルチタブのドキュメント ウィンドウをすべて\] タブは、異なるコマンド コンテキスト GUID を持っています。 ツール ウィンドウは、登録後は、\[利用可能なは常に、 **ビュー** メニュー。  
  
-   **UI コンテキスト** UI コンテキストは、の値によって識別されます、 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> クラス、たとえば、 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> ソリューションをビルドするとき、または <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> 、デバッガーがアクティブな場合です。 複数の UI コンテキストは、同時にアクティブにできません。  
  
## カスタム コンテキストの Guid を定義します。  
 適切なコマンド コンテキストの GUID が定義されていない場合、VSPackage でいずれかを定義し、アクティブまたはコマンドの表示を制御する必要に応じて非アクティブにすることをプログラムできます。  
  
1.  呼び出してコンテキスト Guid を登録、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> メソッドです。  
  
2.  呼び出してコンテキスト GUID の状態を取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> メソッドです。  
  
3.  呼び出してコンテキスト Guid のオンとオフ、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> メソッドです。  
  
    > [!CAUTION]
    >  VSPackage 影響を及ぼさないように既存のコンテキスト Guid vspackages にあるその他の可能性がありますそれらに依存していることを確認します。  
  
## 参照  
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)