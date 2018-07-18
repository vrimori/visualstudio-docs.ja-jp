---
title: '方法: 標準のテキストのマーカーの追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fc5bf34c9b4200d8d7fef2d9f4a878ca604f886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127987"
---
# <a name="how-to-add-standard-text-markers"></a>方法: 標準のテキストのマーカーの追加
提供される既定のテキスト マーカーの種類を作成するのには、次の手順を使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターです。  
  
### <a name="to-create-a-text-marker"></a>テキスト マーカーを作成するには  
  
1.  1 つまたは 2 つの次元座標系、呼び出しのどちらを使用するかどうかによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>新しいテキスト マーカーを作成するメソッド。  
  
     このメソッドの呼び出しで、上でマーカーを作成するテキストの範囲、マーカーの種類を指定し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスです。 このメソッドは、新しく作成されたテキスト マーカーにし、ポインターを返します。 マーカーの種類がから取得した、<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>列挙します。 指定して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスの場合は、マーカーのイベントを通知します。  
  
    > [!NOTE]
    >  のみのメイン UI スレッドでテキスト マーカーを作成します。 テキスト マーカーを作成するためのテキスト バッファーの内容に依存しているコア エディターとテキスト バッファーはスレッド セーフではありません。  
  
## <a name="adding-a-custom-command"></a>カスタム コマンドを追加します。  
 実装する、`IVsTextMarkerClient`インターフェイス/マーカーからへのポインターを提供することは、いくつかの方法でマーカーの動作を拡張します。 最初に、これにより、マーカーのヒントを提供し、コマンドを実行できます。 これによりマーカーは、個別のイベント通知を受信して、マーカーの上のカスタムのコンテキスト メニューを作成するもできます。 マーカー コンテキスト メニューにカスタム コマンドを追加するのにには、次の手順を使用します。  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>コンテキスト メニューにカスタム コマンドを追加するには  
  
1.  環境を呼び出すコンテキスト メニューを表示する前に、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>メソッドとパスをテキスト マーカーへのポインターの影響を受けると、コンテキスト メニュー コマンド項目の数。  
  
     たとえば、コンテキスト メニューで、ブレークポイントに関連するコマンドが含まれて**のブレークポイントを削除**を通じて**新しいブレークポイント**次のスクリーン ショットに表示されています。  
  
     ![マーカー コンテキスト メニュー](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  カスタム コマンドの名前を表すいくつかのテキストを渡します。 たとえば、**ブレークポイントの解除**環境が既に提供されていない場合に、カスタム コマンドがあります。 渡すこともバックアップするかどうかのコマンドは、サポートされている、利用可能で、有効になっている、またはのオン/オフ切り替え。 環境では、この情報を使用して、適切な方法で、コンテキスト メニューで、カスタム コマンドを表示します。  
  
3.  環境の呼び出し、コマンドを実行する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>メソッド、テキスト マーカーおよびコンテキスト メニューから選択したコマンドの数にポインターを渡すことです。  
  
     テキスト マーカーの任意のアクション、カスタム コマンドを決定を実行するのにには、この呼び出しでこの情報を使用します。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)   
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)