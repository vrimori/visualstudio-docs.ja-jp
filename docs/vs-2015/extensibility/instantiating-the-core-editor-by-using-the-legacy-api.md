---
title: レガシ API を使用して、コア エディターをインスタンス化する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e929f46ae6e7f1ef374c663242abb5b332ed4ffb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828443"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>レガシ API を使用して、コア エディターをインスタンス化します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディターはテキストの挿入、削除、コピー、および貼り付けなどの関数を編集します。 テキストの色分け表示、インデント、および IntelliSense ステートメント入力候補などの言語サービスによって提供されると、これらの関数を組み合わせています。  
  
 3 つの方法の 1 つのコア エディターのインスタンスをインスタンス化することができます。  
  
- 明示的にインスタンスを作成、core のエディター ウィンドウにします。  
  
- コア エディターのインスタンスを返すエディター ファクトリを提供します。  
  
- プロジェクトの階層からファイルを開きます。  
  
  次のセクションでは、従来の API を使用して、エディターのインスタンスを作成する方法について説明します。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>コア エディター インスタンスを明示的に開く  
 ときに、コア エディターのインスタンスを明示的に取得するには。  
  
- 取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>編集対象のドキュメント データ オブジェクトを保持するためにします。  
  
- 作成して、ドキュメント データ オブジェクトの行指向の表現を作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイス。  
  
- 設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>の既定の実装のインスタンスのドキュメント データ オブジェクトとして、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インターフェイスを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>メソッド。  
  
   ホスト、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>インスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>メソッド。  
  
  この時点では、表示、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイスには、コア エディターのインスタンスを含むウィンドウが用意されています。  
  
  ただし、これはできません、非常に便利なインスタンスがショートカット キー、または高度な機能にアクセスしません。 ショートカット キーと高度な機能へのアクセスを取得します。  
  
- 使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>言語サービスと、エディターを使用するドキュメント データ オブジェクトに関連付けるメソッド。  
  
- ショートカット キーを作成するかを設定して、システムの既定値を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクトのプロパティを表示します。 これを行うには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>プロパティ。  
  
   取得し、非標準のショートカット キーを使用して、.vsct ファイルを使用してそれらを生成します。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>エディター ファクトリを使用して、コア エディターを取得する方法  
 使用してエディター ファクトリのコア エディターを実装するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを明示的にホストする、前のセクションに記載されているすべての手順に従います、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>ドキュメント データ オブジェクトで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>オブジェクト。  
  
 テキストを表示するには、取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド。  
  
 エディターには、言語サービスを提供するには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>内のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド。  
  
 前のセクションとは異なり、ショートカット キーの既定値を取得するには、によって返されるコマンドのコンテキストを使用する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドからのコア エディターを取得するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド。  
  
 場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドは、テキスト エディターと同じコマンドの GUID を返します、コア エディターのインスタンスがショートカット キーに自動的に既定値に取得します。  
  
 一般的な情報は、次を参照してください。[チュートリアル: コア エディターを作成してエディター ファイルの種類を登録する](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター内で](../extensibility/inside-the-core-editor.md)   
 [開くと、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [チュートリアル: コア エディターの作成とエディター ファイルの種類の登録](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

