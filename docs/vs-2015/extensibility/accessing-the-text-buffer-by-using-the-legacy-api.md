---
title: レガシ API を使用して、テキスト バッファーへのアクセス |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84843f40b6d07e937837914f07aecf10adad2bba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277213"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>レガシ API を使用して、テキスト バッファーにアクセスします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキストがテキスト ストリームとファイルの永続性の管理を担当します。 バッファーの読み取りまたは書き込みの他の形式、バッファーとすべての通常の通信は Unicode を使用して実行します。 従来の Api では、テキスト バッファーは、バッファー内の文字の位置を識別するためにも、1 部または 2 次元座標系に使用できます。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>1 と 2 次元座標系します。  
 1 次元の座標位置は、最初の文字から 147 など、バッファー内の文字の位置に基づきます。 使用する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>バッファー内の 1 次元の場所にアクセスするインターフェイス。 2 次元座標系は、行とインデックスのペアに基づいています。 たとえば、43、バッファー内の文字、5 になります 43、その行の最初の文字の右側に 5 文字の行にします。 バッファーを使用して、2 次元の場所にアクセスする、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>インターフェイス。 両方の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>インターフェイスは、テキスト バッファー オブジェクトによって実装されます (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) を使用して、互いにアクセスできると`QueryInterface`。 次の図は、これらおよびその他のキーのインターフェイスを示しています。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>します。  
  
 ![テキスト バッファー オブジェクト](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
テキスト バッファー オブジェクト  
  
 テキスト バッファーのいずれかの座標システム動作しますが、2 次元座標を使用する最適化されています。 1 次元座標系では、パフォーマンスのオーバーヘッドを作成できます。 そのため、可能な場合は、2 次元座標システムを使用します。  
  
 テキスト バッファーの 2 つ目の責任は、ファイルの永続化します。 テキスト バッファー オブジェクトを実装するのには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>プロジェクト項目のドキュメント データ オブジェクトのコンポーネントと永続化に関連するその他の環境コンポーネントとして機能します。 詳細については、次を参照してください。[とプロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レガシ API を使用する表示設定の変更](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 従来の API を使用して表示設定を変更する方法について説明します。  
  
 [グローバル設定を監視するためのテキスト マネージャーの使用](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 テキスト マネージャーを使用して、グローバル設定を監視する方法について説明します.  
  
## <a name="see-also"></a>関連項目  
 [コア エディターの内部](../extensibility/inside-the-core-editor.md)

