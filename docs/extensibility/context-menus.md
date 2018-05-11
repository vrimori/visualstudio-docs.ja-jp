---
title: コンテキスト メニュー |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus"></a>コンテキスト メニュー
コンテキスト メニューは、ユーザーがクライアント領域のアクティブな領域で右クリックしたときに表示し、マウスの右ボタンが離されたときにクリアします。  
  
## <a name="editor-context-menus"></a>エディター コンテキスト メニュー  
 インターセプトして`ECMD_SHOWCONTEXTMENU`、言語サービスは、エディターに表示されるコンテキスト メニューを制御できます。 表示するには、独自のコンテキスト メニューに渡されるときにこのコマンドを処理して<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>を呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>です。 このコマンドを処理しない場合は、エディターの提供される標準のコンテキスト メニューが表示されます。 マーカーあたりごとに、コンテキスト メニューの内容を制御することもできます。 詳細については、次を参照してください。[レガシ API でテキスト マーカーを使用して](../extensibility/using-text-markers-with-the-legacy-api.md)と[レガシ言語サービス コマンドの傍受](../extensibility/internals/intercepting-legacy-language-service-commands.md)です。  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)   
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)