---
title: "相互運用機能アセンブリを使用してコマンドのステータスを決定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3cde6ae841271622e0d538d679991288c111095e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>相互運用機能アセンブリを使用してコマンドのステータスを決定します。
VSPackage 必要がありますの追跡を処理できるコマンドの状態。 ときに VSPackage 内で処理コマンドを有効または無効になります、環境を特定できません。 コマンドの状態について、環境を通知するために VSPackage の責任は、たとえば、[全般] の状態などのコマンド**切り取り**、**コピー**、および**貼り付け**です。  
  
## <a name="status-notification-sources"></a>状態通知のソース  
 環境は、Vspackage のを通じてコマンドに関する情報を受け取る<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>VSPackage の実装の一部であるメソッドの<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 環境の呼び出し、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 2 つの条件下で、VSPackage のメソッド。  
  
-   ユーザーがメイン メニューまたはコンテキスト メニューを開く (を右クリックして)、環境が実行される、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>の状態をメニューのコマンドのすべてのメソッドです。  
  
-   ときに、VSPackage は、環境が現在のユーザー インターフェイス (UI) を更新することを要求します。 などで、ユーザーに現在表示されているコマンドとこれが発生した、**切り取り**、**コピー**、および**貼り付け**[標準] ツールバーをグループ化、有効になっているなりで無効になっていますコンテキストとユーザーの操作に対する応答です。  
  
 シェルは、複数の Vspackage をホストしているため、シェルのパフォーマンスが容認できないほどが低下する場合は、コマンドの状態を判断する VSPackage ごとにポーリングする必要があります。 代わりに、変更時に、UI が変更されたときに、VSPackage は、環境を通知アクティブにする必要があります。 更新の通知の詳細については、次を参照してください。[ユーザー インターフェイスを更新して](../../extensibility/updating-the-user-interface.md)です。  
  
## <a name="status-notification-failure"></a>状態の通知エラー  
 VSPackage のコマンドの状態変更の環境に通知するエラーは、不整合な状態に UI を配置できます。 メニューまたはコンテキスト メニュー コマンドのいずれかのことができますに配置すること、ツールバーで、ユーザーが注意してください。 そのため、メニューまたはコンテキスト メニューを開いたときにのみ、UI の更新は不十分です。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../../extensibility/internals/command-implementation.md)