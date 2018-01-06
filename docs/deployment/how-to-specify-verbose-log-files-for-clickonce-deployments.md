---
title: "方法: ClickOnce の配置の詳細なログ ファイルを指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6cac7764a941e88dd3901a3280e78717955e86b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>方法: ClickOnce 配置用の詳細ログ ファイルを指定する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]すべての展開のアクティビティ ログ ファイルを保持します。 これらのログ記録の詳細、関連するインストールの初期化中、更新、アンインストール、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 詳細を向上させるを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]これらのログ ファイルへの書き込みは、レジストリ エディタを使用して (**regedit.exe**) 詳細レベルを指定します。  
  
> [!CAUTION]
>  レジストリ エディターを誤って使用する場合、オペレーティング システムを再インストールする必要があります深刻な問題が発生する可能性があります。 問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
 次の手順の詳細レベルを指定する方法を説明する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]現在のユーザーのログ ファイルです。 詳細度のレベルを減らすためには、このレジストリ値を削除します。  
  
### <a name="to-specify-verbose-log-files"></a>詳細ログ ファイルを指定するには  
  
1.  開いている**Regedit.exe**です。  
  
2.  ノードに移動`HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`です。  
  
3.  必要に応じて、という名前の新しい文字列値を作成`LogVerbosityLevel`です。  
  
4.  設定、`LogVerbosityLevel`値を`1`です。  
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)