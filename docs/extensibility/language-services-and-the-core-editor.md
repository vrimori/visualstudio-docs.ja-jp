---
title: 言語サービスとコア エディター |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7f439cf1564e14857b3a609191cc0bea05e0e04
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636240"
---
# <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター
Visual Studio のエディターは、言語サービスに頻繁に関連付けられます。 その他のものは、言語サービスは、構文の色分け表示、ステートメント入力候補、IntelliSense、およびテキストの書式設定を提供します。  
  
## <a name="core-editors-and-document-data-objects"></a>コア エディターやドキュメント データ オブジェクト  
 コア エディターにアクセスする場合は、ドキュメント データとドキュメント ビュー オブジェクトは作成しません。 作成され、これら 2 つのオブジェクトを制御し、エディター ファクトリの実装で適切な呼び出しを作成してそれらへのハンドルを取得します。  
  
 詳細については、次を参照してください。[エディターがプロジェクトでファイルを開きます決定](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)します。  
  
## <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター  
 言語サービスを実装すると、ドキュメント ビューでデータを表示する方法を制御できます。 言語サービスは、情報とは、Visual C などの特定の言語に固有の動作を提供します。 テキスト バッファーが、レジストリ キーからこのファイル名拡張子に関連付けられた言語サービスを決定するテキスト バッファーを作成して開いているドキュメントのファイル名拡張子を決定する**HKEY_LOCAL_MACHINEMicrosoft\Editors\\YourLanguageService {GUID} \Extensions**します。 プロシージャを読み込み、標準の VSPackage は、VSPackage を読み込むし、言語サービスのインスタンスが作成されます。  
  
 基本的な言語サービスは、次の図に表示されます。  
  
 ![言語サービス モデル グラフィック](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
コア エディターと言語サービスのオブジェクト  
  
 コア エディター ドキュメント データ オブジェクトを選択してテキスト バッファーを呼びますで表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクト。 ドキュメント ビュー オブジェクトを選択してテキスト ビューを呼びますで表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>オブジェクト。 これら 2 つのオブジェクトは、コア エディターの統合ビューを提供する言語サービスを介して連携します。 テキスト バッファーと、ドキュメント ウィンドウにテキスト ビューに表示される情報には、コード ウィンドウが呼び出されます。 コード ウィンドウのドキュメントは、コード ウィンドウ マネージャーによって管理されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [従来の API を使用して、言語サービスのコンテキストを提供します。](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense をホストしています。](../extensibility/intellisense-hosting.md)   
 [含まれている言語](../extensibility/contained-languages.md)   
 [従来の言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md)