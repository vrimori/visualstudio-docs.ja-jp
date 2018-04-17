---
title: '方法: ClickOnce の配置の詳細なログ ファイルを指定する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b478c7ef7c883b21e77f2e3768c96a9f33383469
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>方法: ClickOnce 配置用の詳細ログ ファイルを指定する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] すべての展開のアクティビティ ログ ファイルを保持します。 これらのログ記録の詳細、関連するインストールの初期化中、更新、アンインストール、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 詳細を向上させるを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]これらのログ ファイルへの書き込みは、レジストリ エディタを使用して (**regedit.exe**) 詳細レベルを指定します。  
  
> [!CAUTION]
>  レジストリ エディターを誤って使用する場合、オペレーティング システムを再インストールする必要があります深刻な問題が発生する可能性があります。 問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
 次の手順の詳細レベルを指定する方法を説明する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]現在のユーザーのログ ファイルです。 詳細度のレベルを減らすためには、このレジストリ値を削除します。  
  
### <a name="to-specify-verbose-log-files"></a>詳細ログ ファイルを指定するには  
  
1.  開いている**Regedit.exe**です。  
  
2.  ノードに移動`HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`です。  
  
3.  必要に応じて、という名前の新しい文字列値を作成`LogVerbosityLevel`です。  
  
4.  設定、`LogVerbosityLevel`値を`1`です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)