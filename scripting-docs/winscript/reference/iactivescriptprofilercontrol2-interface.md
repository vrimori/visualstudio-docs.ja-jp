---
title: "IActiveScriptProfilerControl2 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bc0dfa31b37a6bf99427c8eddfe2bd038da9b9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 インターフェイス
開始または停止するスクリプトが実行されている場合をプロファイリングする機能を追加するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|すべての該当するスクリプト エンジンでプロファイリングを開始したことをプロファイラーに通知します。 これは、ようにする場合は、完全なコール スタックを取得[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]プロファイリングを開始するときに実行します。|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|適用可能なすべてのスクリプト エンジンでプロファイリングを停止しようとしていることをプロファイラーに通知します。 これによりの場合は、完全な呼び出し履歴を取得する[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]が実行されているは、プロファイリングを停止するとします。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerControl インターフェイス](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)