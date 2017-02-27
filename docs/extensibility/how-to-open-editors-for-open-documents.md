---
title: "方法: 開いているドキュメントのエディターを開く | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "開いているドキュメントを開くエディター [Visual Studio SDK]"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 方法: 開いているドキュメントのエディターを開く
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクトがドキュメント ウィンドウを開く前に最初にファイルが既に別のエディターのドキュメント ウィンドウで開いているかどうかを判断します。  ファイルはプロジェクトに固有のエディターが開き[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に登録されている標準エディターの 1 種類のいずれかです。  
  
## プロジェクト固有のエディターを開く  
 既に開いているファイル用のプロジェクト固有のエディターを開くには次の手順を使用します。  
  
#### 開いているファイルのプロジェクト固有のエディターを開きます。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> メソッドを呼び出します。  
  
     この呼び出しはドキュメントの階層階層内の項目とフレーム ウィンドウに応じてポインターを返します。  
  
2.  ドキュメントが開かれている場合は確認する必要があります。ドキュメント データ オブジェクトだけに存在するかどうかはプロジェクトがドキュメントのビュー オブジェクトにするかどうか。  
  
    -   ドキュメントのビュー オブジェクトでありこのビューには階層または階層の項目の場合はビューのウィンドウ枠既存のウィンドウに新しい表紙を付けるにはポインターを使用します。  
  
    -   ドキュメントのビュー オブジェクトがある場合このビューが同じ階層および階層内の項目の場合はプロジェクト ドキュメントは基になるデータ オブジェクトにアタッチできる 2 番目のビューを開くことができます。  はビューのウィンドウ枠既存のウィンドウに新しい表紙を付けるにはポインターを使用する必要があります。  
  
    -   ドキュメント データ オブジェクトだけの場合プロジェクトはビューのドキュメント データ オブジェクトが使用できるかどうかを判断する必要があります。  ドキュメント データ オブジェクトは互換性のある[プロジェクト固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md) で説明した手順を実行します。  
  
     ドキュメント データ オブジェクトに互換性がない場合エラーはユーザーにファイルは現在使用中であるとが表示されます。  このエラーは一時的なケースでファイルを同時にユーザー [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコア エディターのテキスト エディターを使用してファイルを開こうとしている場合にのみコンパイルなどの表示されます。  コア テキスト エディターはドキュメント データ オブジェクトを共有できます。  
  
3.  ドキュメントのデータ オブジェクトまたはドキュメントのビュー オブジェクトがないためドキュメントが開いていない場合は[プロジェクト固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md) の手順を実行します。  
  
## 標準エディターを開く  
 既に開いているファイルの標準エディターを開くには次の手順を使用します。  
  
#### 開いているファイルの標準エディターを開きます。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> を呼び出します。  
  
     このメソッドは最初にドキュメントが既に <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> を呼び出すことによって開かれていないことを確認します。  ドキュメントが開いている場合はエディター ウィンドウは新しい表紙が付けられます。  
  
2.  ドキュメントが開いていない場合はを [方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md) の手順を実行します。  
  
## 参照  
 [開く、プロジェクト項目を保存します。](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md)