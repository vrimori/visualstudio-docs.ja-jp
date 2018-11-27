---
title: VSTextBuffer オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987514f20746b8480391a35d7a9c9a9d3663cac2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728786"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer オブジェクト
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキスト バッファー オブジェクトは、Unicode テキストは、一般には、ファイルのストリームを表します。 A<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ウィザード場合と同様、コア エディターのコンテキスト外にあるオブジェクトを使用できます。  
  
 次の表は、インターフェイスの`VSTextBuffer`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|標準の OLE インターフェイス。 主に、元に戻す/やり直しのバッファーでの処理で使用します。|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|標準の OLE インターフェイス。|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|標準の OLE インターフェイス。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|複合語、アクション (つまり、元に戻す/やり直しの 1 つの単位にグループ化されるアクション) を作成できます。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|テキスト バッファーによって管理されるドキュメントのデータの永続化を有効にします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|基本的なサービスを提供します。多くのクライアントによって使用されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|バッファーを検索するために使用します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|読み取りし、書き込みの 2 次元座標を使用して機能します。 `IVsTextBuffer`から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|読み取りし、書き込みの 1 次元の座標を使用して機能します。 `IVsTextBuffer`から継承します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|高速で、バッファー内のテキストをストリーム指向、シーケンシャル アクセスを提供します。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|プロパティのジェネリック コレクションへのアクセスを提供します。 最も重要なプロパティは、名前、またはバッファーのモニカーです。 GUID の作成、キーとして使用して、このインターフェイスでバッファーのランダム データを格納できます。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|イベントのコネクション ポイントをサポートしています。|  
  
## <a name="remarks"></a>Remarks  
 `VSTextBuffer`で見つかることが、`QueryInterface`で呼び出す`IVsTextBuffer`します。 詳細については、次を参照してください。[テキスト バッファー](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [図の編集](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)

