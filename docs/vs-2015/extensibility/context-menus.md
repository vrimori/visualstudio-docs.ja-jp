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
ms.openlocfilehash: efd4e1c80b9af2a0d73730f0bd7d741cd877fb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796845"
---
# <a name="context-menus"></a>コンテキスト メニュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンテキスト メニューでは、クライアント領域のアクティブなリージョンでユーザーを右クリックしたときに表示され、マウスの右ボタンが離されたときをオフにします。  
  
## <a name="editor-context-menus"></a>エディター コンテキスト メニュー  
 インターセプトすることで`ECMD_SHOWCONTEXTMENU`、言語サービスは、エディターに表示されるコンテキスト メニューを制御できます。 独自のコンテキスト メニューを表示するには、次のコマンド処理に渡されると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>します。 このコマンドを処理しない場合は、エディターの提供される標準のコンテキスト メニューが表示されます。 マーカーあたりごとに、コンテキスト メニューの内容を制御することもできます。 詳細については、次を参照してください。[レガシ API を使用したテキスト マーカーを使用して](../extensibility/using-text-markers-with-the-legacy-api.md)と[レガシ言語サービス コマンドのインターセプト](../extensibility/internals/intercepting-legacy-language-service-commands.md)します。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)   
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)

