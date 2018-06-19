---
title: 従来の言語サービスのモデル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 943f0f013045e3082af3069ed4d45aaed1096869
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131588"
---
# <a name="model-of-a-legacy-language-service"></a>従来の言語サービスのモデル
言語サービスは、要素と、特定の言語の機能を定義し、その言語に固有の情報に、エディターを提供するために使用します。 たとえば、エディターは、構文の色分けをサポートするために、要素と言語のキーワードを知っている必要があります。  
  
 言語サービスは、エディターと、エディターを含むビューによって管理されるテキスト バッファーと緊密に動作します。 Microsoft IntelliSense**クイック ヒント**オプションが言語サービスによって提供される機能の例を示します。  
  
## <a name="a-minimal-language-service"></a>最小限の言語サービス  
 最も基本的な言語サービスには、次の 2 つのオブジェクトが含まれています。  
  
-   *言語サービス*を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスです。 言語サービスには、名前、ファイル名拡張子、コード ウィンドウ マネージャー、および colorizer など、言語に関する情報があります。  
  
-   *Colorizer*を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスです。  
  
 次の概念図は、基本的な言語サービスのモデルを示しています。  
  
 ![言語サービス モデル グラフィック](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本的な言語サービス モデル  
  
 ドキュメント ウィンドウのホスト、*文書の表示*ここでは、エディターの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コア エディターです。 ドキュメントの表示とテキスト バッファーは、エディターによって所有されます。 これらのオブジェクトを使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と呼ばれる特殊なドキュメント ウィンドウで、*コード ウィンドウ*します。 コード ウィンドウに含まれている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>が作成され、IDE によって制御されるオブジェクト。  
  
 エディターがその拡張子に関連付けられた言語サービスを検索し、呼び出すことによって、コード ウィンドウを渡します指定された拡張子を持つファイルが読み込まれるときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>メソッドです。 言語サービスを返します、*コード ウィンドウ マネージャー*を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイスです。  
  
 次の表は、モデル内のオブジェクトの概要を示します。  
  
|コンポーネント|Object|関数|  
|---------------|------------|--------------|  
|テキスト バッファー|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode の読み取り/書き込みテキスト ストリーム。 その他のエンコーディングを使用するテキストのことができます。|  
|コード ウィンドウ|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|1 つまたは複数のテキスト ビューを含むドキュメント ウィンドウです。 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]がマルチ ドキュメント インターフェイス (MDI) モードでは、コード ウィンドウの MDI 子。|  
|テキスト ビュー|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|ユーザーが移動し、キーボードとマウスを使用してテキストを表示できるウィンドウです。 テキスト ビューは、エディターとしてユーザーに表示されます。 通常のエディター ウィンドウ、出力ウィンドウおよびイミディ エイト ウィンドウでテキスト ビューを使用することができます。 さらに、コード ウィンドウ内の 1 つ以上のテキスト ビューを構成することができます。|  
|テキスト マネージャー|によって管理される、<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>から取得する、サービス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>ポインター|前に説明したすべてのコンポーネントで共有される共通の情報を保持するためのコンポーネント。|  
|言語サービス|実装に依存します。実装します。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|構文の強調表示、ステートメント入力候補、かっこの照合などの言語に固有の情報と、エディターを提供するオブジェクト。|  
  
## <a name="see-also"></a>関連項目  
 [カスタム エディターでのドキュメント データとドキュメント ビュー](../../extensibility/document-data-and-document-view-in-custom-editors.md)