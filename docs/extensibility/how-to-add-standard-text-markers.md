---
title: '方法: 標準のテキスト マーカーの追加 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80c32827a991a87b582f31ceefd2bfd6dbcc7a8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922351"
---
# <a name="how-to-add-standard-text-markers"></a>方法: 標準のテキスト マーカーを追加します。
次の手順を使用して、提供される既定のテキスト マーカーの種類のいずれかを作成する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディター。  
  
## <a name="to-create-a-text-marker"></a>テキスト マーカーを作成するには  
  
1.  1 つまたは 2 次元座標系を使用するかに応じて呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>メソッドまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>新しいテキスト マーカーを作成します。  
  
     このメソッド呼び出しで、マーカーの種類、マーカーを作成するテキストの範囲を指定し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイス。 このメソッドは、新しく作成されたテキスト マーカーにし、ポインターを返します。 マーカーの種類がから取得した、<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>列挙体。 指定、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスのマーカー イベントを通知する場合。  
  
    > [!NOTE]
    >  テキスト マーカーは、メイン UI スレッドでのみで作成します。 テキスト マーカーを作成するためのテキスト バッファーの内容に基づいて、コア エディターとテキスト バッファーはスレッド セーフではありません。  
  
## <a name="add-a-custom-command"></a>カスタム コマンドの追加  
 実装する、`IVsTextMarkerClient`インターフェイスとをマーカーからのポインターを提供するいくつかの方法でマーカー動作が向上します。 最初に、これにより、マーカーのヒントを紹介し、コマンドを実行できます。 これによりマーカーは、個別のイベント通知を受信して、マーカーの上でカスタム コンテキスト メニューを作成することもできます。 マーカー コンテキスト メニューにカスタム コマンドを追加するのにには、次の手順を使用します。  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>コンテキスト メニューにカスタム コマンドを追加するには  
  
1.  コンテキスト メニューが表示される前に、環境を呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>メソッドと影響を受けるテキスト マーカーへのポインターを渡すと、コンテキスト メニュー コマンド項目の数。  
  
     たとえば、コンテキスト メニューの ブレークポイントに固有のコマンドが含まれて**ブレークポイントの削除**を通じて**新しいブレークポイント**次のスクリーン ショットに表示されています。  
  
     ![マーカー コンテキスト メニュー](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  カスタム コマンドの名前を識別するテキストをパスにバックアップします。 たとえば、**ブレークポイントの削除**環境が既に提供していない場合、カスタム コマンドがあります。 戻る渡すことも、コマンドは、サポートされている、使用可能なおよび有効にするかどうかや、オン/オフ切り替え。 環境では、この情報を使用して、適切な方法で、コンテキスト メニューにカスタム コマンドを表示します。  
  
3.  環境は、コマンドを実行する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>テキスト マーカーをコンテキスト メニューから選択したコマンドの数のポインターを渡してメソッド。  
  
     テキスト マーカーの任意のアクション、カスタム コマンドの指示を実行するのにには、この呼び出しでこの情報を使用します。  
  
## <a name="see-also"></a>関連項目  
 [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: エラーのマーカーを実装します。](../extensibility/how-to-implement-error-markers.md)   
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキスト マーカーを使用します。](../extensibility/how-to-use-text-markers.md)