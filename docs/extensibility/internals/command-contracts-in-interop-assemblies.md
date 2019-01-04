---
title: 相互運用機能アセンブリ内のコントラクトをコマンド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3c6aea16308c39679c9e31043998b0c6c5558cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892992"
---
# <a name="command-contracts-in-interop-assemblies"></a>相互運用機能アセンブリでのコマンドのコントラクト
使ってコマンドを処理するための基本的なコントラクト、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスは、環境を呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドがサポートされている場合と、コマンドがサポートされているかどうかを判断する、その状態とテキストを決定します。 次に、環境は、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>コマンドを実行するメソッド。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドは、すべてのコマンドと同じ処理されます。 それ以降の通信は (たとえば、ドロップ ダウン リストの場合) に必要な場合、呼び出すことによって管理されます、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>適切なパラメーターを持つメソッド。 これらのパラメーターの解釈は、指定されたコマンドに依存します。  
  
 場合は、コマンド ターゲットでは、出力パラメーターの値を返します、呼び出し元が割り当てられているすべてのリソースの解放を常にします。 このパラメーターは、バリアントはバリアントをオフにすると、リソースを解放します。  
  
 コマンドが、階層ウィンドウ内で動作する必要がの場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスを使用する必要があります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスが同様のメソッドと類似のコントラクト:<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>します。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)   
 [コマンドの実装](../../extensibility/internals/command-implementation.md)