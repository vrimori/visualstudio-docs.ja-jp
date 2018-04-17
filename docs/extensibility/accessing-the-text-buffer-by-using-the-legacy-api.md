---
title: レガシ API を使用してテキスト バッファーにアクセスする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84bf79ea19fc0867643ce3e8ee6db0a645d9a0dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>レガシ API を使用してテキスト バッファーにアクセスします。
テキストがテキスト ストリームとファイルの永続性の管理を担当します。 バッファーの読み取りまたはその他の形式を書き込み、すべての通常の通信バッファーと Unicode を使用して実行されます。 従来の Api でテキスト バッファーは、バッファー内の文字の位置を識別するのに 1 つのまたは 2 次元座標系を使用できます。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>1 と 2 次元座標系します。  
 1 次元座標位置は、最初の文字から 147 など、バッファー内の文字の位置に基づいています。 使用する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>バッファー内の 1 次元の場所にアクセスするインターフェイスです。 2 次元座標系は、行とインデックスの組み合わせに基づいています。 たとえば、43、バッファー内の文字、5 は行に指定 43、その行の最初の文字の右側に 5 つの文字。 バッファーを使用して、2 次元の場所にアクセスする、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>インターフェイスです。 両方の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>インターフェイスは、テキスト バッファー オブジェクトによって実装されて (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) を使用して互いからアクセス可能`QueryInterface`です。 次の図は、これらおよび他のキーのインターフェイスを示しています。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>です。  
  
 ![テキスト バッファー オブジェクト](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
テキスト バッファー オブジェクト  
  
 テキスト バッファーのいずれかの座標系動作しますが、2 次元座標を使用する最適です。 1 次元座標系では、パフォーマンスのオーバーヘッドを作成できます。 したがって、可能な場合は、2 次元座標システムを使用します。  
  
 テキスト バッファーの 2 つ目の責任は、ファイルの永続化します。 テキスト バッファー オブジェクトを実装してこれを行うには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>し、プロジェクト項目のドキュメント データ オブジェクトのコンポーネントおよび永続化に関連するその他の環境コンポーネントとして機能します。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 従来の API を使用して表示設定を変更する方法について説明します。  
  
 [テキスト マネージャーを使用して、グローバル設定を監視するには](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 テキスト マネージャーを使用して、グローバル設定を監視する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター内](../extensibility/inside-the-core-editor.md)