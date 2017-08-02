---
title: "言語サービスとコア エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
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
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター
Visual Studio でのエディターは、言語サービスに頻繁に関連付けられます。 特には、言語サービスは、構文の色分け表示、ステートメント入力候補、IntelliSense、およびテキストの書式設定を提供します。  
  
## <a name="core-editors-and-document-data-objects"></a>コア エディターやドキュメントのデータ オブジェクト  
 コア エディターにアクセスする場合は、ドキュメント データおよびドキュメント ビューのオブジェクトは作成しません。 作成され、これら&2; つのオブジェクトを制御し、ファクトリの実装をエディターでの適切な呼び出しを行うことによりそれらへのハンドルを取得します。  
  
 詳細については、次を参照してください。[プロジェクトでファイルを開くエディターを決定する](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)です。  
  
## <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター  
 言語サービスを実装することで、ドキュメント ビューでデータを表示する方法を制御できます。 言語サービスは、情報とは、Visual C などの特定の言語に固有の動作を示します。 テキスト バッファーが HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors のレジストリ キーからファイル名の拡張子に関連付けられた言語サービスを決定するテキスト バッファーを作成して開いているドキュメントのファイル名拡張子を決定する\\YourLanguageService {GUID} \Extensions します。 標準の VSPackage プロシージャを読み込みは、VSPackage を読み込んで、言語サービスのインスタンスを作成します。  
  
 基本的な言語サービスは、次の図に示されています。  
  
 ![言語サービス モデル グラフィック](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
コア エディターと言語のサービス オブジェクト  
  
 コア エディター ドキュメントのデータ オブジェクトし、呼ばれ、バッファーにテキストで表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。 ドキュメント ビューのオブジェクトし、呼ばれ、テキスト ビューによって表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>オブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>。 これら&2; つのオブジェクトは連携してコア エディターの統一されたビューを提供する言語サービスを使用します。 テキスト バッファーと、ドキュメント ウィンドウにテキスト ビューに表示からの情報には、コード ウィンドウが呼び出されます。 コード ウィンドウのドキュメントは、コード ウィンドウ マネージャーによって管理されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [レガシ API を使用して、言語サービスのコンテキストを提供します。](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense をホストしています。](../extensibility/intellisense-hosting.md)   
 [格納されている言語](../extensibility/contained-languages.md)   
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)
