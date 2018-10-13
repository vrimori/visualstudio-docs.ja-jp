---
title: コンテキスト メニュー |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4b53174776b93d94c38982a430db3213ba184b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207730"
---
# <a name="context-menus"></a>コンテキスト メニュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンテキスト メニューでは、クライアント領域のアクティブなリージョンでユーザーを右クリックしたときに表示され、マウスの右ボタンが離されたときをオフにします。  
  
## <a name="editor-context-menus"></a>エディター コンテキスト メニュー  
 インターセプトすることで`ECMD_SHOWCONTEXTMENU`、言語サービスは、エディターに表示されるコンテキスト メニューを制御できます。 独自のコンテキスト メニューを表示するには、次のコマンド処理に渡されると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>します。 このコマンドを処理しない場合は、エディターの提供される標準のコンテキスト メニューが表示されます。 マーカーあたりごとに、コンテキスト メニューの内容を制御することもできます。 詳細については、次を参照してください。[レガシ API を使用したテキスト マーカーを使用して](../extensibility/using-text-markers-with-the-legacy-api.md)と[レガシ言語サービス コマンドのインターセプト](../extensibility/internals/intercepting-legacy-language-service-commands.md)します。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)   
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)

