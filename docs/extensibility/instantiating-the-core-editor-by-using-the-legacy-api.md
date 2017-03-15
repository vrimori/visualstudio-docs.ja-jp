---
title: "コア エディターのレガシ API を使用してインスタンス化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>レガシ API を使用してコア エディターをインスタンス化します。
エディターでは、テキストの挿入、削除、コピー、および貼り付けなどの編集機能を担当します。 テキストの色指定、インデント、および IntelliSense のステートメント入力候補などの言語サービスによって提供されると、これらの関数を組み合わせています。  
  
 次の&3; つの方法のいずれかのコア エディターのインスタンスをインスタンス化することができます。  
  
-   明示的にインスタンスを作成、コアのエディター ウィンドウで。  
  
-   コア エディターのインスタンスを返すエディター ファクトリを提供します。  
  
-   プロジェクトの階層からファイルを開きます。  
  
 次のセクションでは、従来の API を使用して、エディターのインスタンスを作成する方法について説明します。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>コア エディター インスタンスを明示的に開く  
 コア エディターのインスタンスを明示的に取得するには: 場合  
  
-   取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>編集されているドキュメントのデータ オブジェクトを保持する</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。  
  
-   作成することで、ドキュメントのデータ オブジェクトの行指向の表現を作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。  
  
-   設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>の既定の実装のインスタンスのドキュメントのデータ オブジェクトとして、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インターフェイスを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。  
  
     ホスト、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。  
  
 この時点では、表示、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスには、コア エディターのインスタンスを含むウィンドウが用意されています</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>。  
  
 ただし、これは非常に便利なインスタンス、ショートカット キーを設定したり、高度な機能にアクセスしないためです。 ショートカット キーと高度な機能にアクセスするには。  
  
-   使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>言語サービスと、エディターを使用するドキュメントのデータ オブジェクトに関連付けるメソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>。  
  
-   ショートカット キーを作成するか、システムの既定値を使用して設定して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクトのプロパティを表示します</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>。 これを行うには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>プロパティ</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>。  
  
     取得し、非標準のショートカット キーを使用してを .vsct ファイルを使用してそれらを生成します。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>エディター ファクトリを使用してコア エディターを取得する方法  
 コア エディターを使用するエディター ファクトリを実装するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを明示的にホストする前のセクションで説明されているすべての手順に従います、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>ドキュメント データ オブジェクトで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクト</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
 表示するには、テキストを取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
 エディターには、言語サービスを提供するには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>内のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>。  
  
 返されたコマンドのコンテキストを使用する、前のセクションとは異なり、ショートカット キーを取得するには、既定値を<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドからコア エディターを取得するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドは、テキスト エディターと同じコマンドの GUID を返しますとは、コア エディターのインスタンスに自動的に取得、既定のショートカット キー。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。  
  
 一般情報は、次を参照してください。[チュートリアル: コア エディターを作成およびエディター ファイルの種類を登録する](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)です。  
  
## <a name="see-also"></a>関連項目  
 [コア エディターの内部](../extensibility/inside-the-core-editor.md)   
 [開く、プロジェクト項目を保存します。](../extensibility/internals/opening-and-saving-project-items.md)   
 [チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
