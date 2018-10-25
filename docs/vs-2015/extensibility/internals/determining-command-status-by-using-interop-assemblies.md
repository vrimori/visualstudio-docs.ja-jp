---
title: 相互運用機能アセンブリを使用してコマンドのステータスの特定 |Microsoft Docs
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
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8871793d27366771978b2cb23284d1dbe5f4dc5a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948253"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>相互運用機能アセンブリを使用したコマンドのステータスの特定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage をする必要がありますの追跡を処理できるコマンドの状態。 場合、VSPackage 内で処理コマンドを有効または無効になります、環境を特定できません。 コマンドの状態について、環境に通知するために VSPackage の責任は、たとえば、[全般] の状態などのコマンド**切り取り**、**コピー**、および**貼り付け**します。  
  
## <a name="status-notification-sources"></a>状態通知のソース  
 環境は、Vspackage のを通じてコマンドに関する情報を受け取る<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>、VSPackage の実装の一部であるメソッドの<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 環境は、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 2 つの条件下で、VSPackage のメソッド。  
  
- ユーザーがメイン メニューまたはコンテキスト メニューを開く (を右クリック)、環境を実行、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>の状態を確認するには、そのメニューのコマンドのすべてのメソッド。  
  
- 場合、VSPackage は、環境が現在のユーザー インターフェイス (UI) を更新することを要求します。 などで、ユーザーに現在表示されているコマンドとこれが発生した、**切り取り**、**コピー**、および**貼り付け**[標準] ツールバーをグループ化、有効になっているなりで無効になっていますコンテキストやユーザー操作に対する応答です。  
  
  シェルは、複数の Vspackage をホストするため、シェルのパフォーマンスは許容範囲を超えるが低下する場合は、コマンドの状態を確認するには、各 VSPackage をポーリングする必要があります。 代わりに、変更時に、UI が変更されたときに、VSPackage は、環境を通知アクティブにする必要があります。 更新の通知の詳細については、次を参照してください。[ユーザー インターフェイスの更新](../../extensibility/updating-the-user-interface.md)します。  
  
## <a name="status-notification-failure"></a>エラーの通知状態  
 コマンドの状態変更の環境に通知する、VSPackage のエラーは、一貫性のない状態で UI を配置できます。 メニューまたはコンテキスト メニュー コマンドのいずれかのことができますに配置すること、ツールバーのユーザーが注意してください。 そのため、メニューまたはコンテキスト メニューを開いたときにのみ、UI の更新は不十分です。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../../extensibility/internals/command-implementation.md)

