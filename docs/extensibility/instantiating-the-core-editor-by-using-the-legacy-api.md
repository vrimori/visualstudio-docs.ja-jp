---
title: "コア エディターのレガシ API を使用してインスタンス化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e508bda0b22c798246b0f6abf4dfb03c41a92d6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>レガシ API を使用して、コア エディターをインスタンス化します。
エディターはテキストの挿入、削除、コピー、および貼り付けなどの関数を編集します。 テキストの色指定、インデント、および IntelliSense 入力候補などの言語サービスによって提供されると、これらの関数を組み合わせています。  
  
 3 つの方法のいずれかでコア エディターのインスタンスをインスタンス化することができます。  
  
-   明示的にインスタンスを作成、コアのエディター ウィンドウにします。  
  
-   コア エディターのインスタンスを返すエディター ファクトリを提供します。  
  
-   プロジェクト階層から、ファイルを開きます。  
  
 次のセクションでは、従来の API を使用して、エディターのインスタンスを作成する方法について説明します。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>コア エディター インスタンスを明示的に開く  
 コア エディターのインスタンスを明示的に取得するには: 場合  
  
-   取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>編集されているドキュメント データ オブジェクトを保持します。  
  
-   作成することで、ドキュメント データ オブジェクトの行指向表記を作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイスです。  
  
-   設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>、ドキュメント データ オブジェクトの既定の実装のインスタンスの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インターフェイスを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>メソッドです。  
  
     ホスト、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>メソッドです。  
  
 この時点では、表示、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスには、コア エディターのインスタンスを含むウィンドウが用意されています。  
  
 ただし、これは非常に便利ですインスタンス、ショートカット キーを持つしたり、高度な機能にアクセスしないためです。 ショートカット キーと高度な機能へのアクセスを取得します。  
  
-   使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>言語サービスと、エディターを使用するドキュメント データ オブジェクトに関連付けるメソッド。  
  
-   ショートカット キーを作成するか、システムの既定値を使用して設定して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクトのプロパティを表示します。 これを行うには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>プロパティです。  
  
     取得し、非標準のショートカット キーを使用するには、.vsct ファイルを使用してそれらを生成します。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>エディター ファクトリを使用して、コア エディターを取得する方法  
 エディター ファクトリを使用してでのコア エディターを実装する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを明示的にホストする、前のセクションで説明されているすべての手順に従って、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>ドキュメント データ オブジェクトで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクト。  
  
 表示するには、テキストを取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドです。  
  
 エディターに言語サービスを提供するには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッド内で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドです。  
  
 既定値に、前のセクションとは異なり、ショートカット キーを取得するには、によって返されるコマンド コンテキストを使用する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドからコア エディターを取得するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドです。  
  
 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドは、テキスト エディターと同じコマンドの GUID を返します、コア エディターのインスタンスを自動的に取得、既定のショートカット キー。  
  
 一般情報は、次を参照してください。[チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録する](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)です。  
  
## <a name="see-also"></a>参照  
 [コア エディター内](../extensibility/inside-the-core-editor.md)   
 [開くと、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)