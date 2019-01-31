---
title: '方法: ClickOnce 配置用の詳細ログ ファイルの指定 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e9abdd886215582d2f4a05145ab9da5bd81151b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041361"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>方法: ClickOnce 配置用の詳細ログ ファイルを指定する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] すべてのデプロイ アクティビティのログ ファイルを保持します。 これらのログ記録に関連するインストール、初期化、更新、およびアンインストールの詳細、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 詳細を向上させるを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]レジストリ エディターを使用して、これらのログ ファイルへの書き込み (*regedit.exe*) 詳細レベルを指定します。  
  
> [!CAUTION]
>  レジストリ エディターを正しく使用する場合、オペレーティング システムを再インストールする必要があります深刻な問題が発生する可能性があります。 問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
 次の手順の詳細レベルを指定する方法を説明する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]現在のユーザーのログ ファイル。 詳細出力レベルを減らすためには、このレジストリ値を削除します。  
  
### <a name="to-specify-verbose-log-files"></a>詳細なログ ファイルを指定するには  
  
1.  開いている*Regedit.exe*します。  
  
2.  ノードに移動**HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**します。  
  
3.  必要に応じて、という名前の新しい文字列値を作成`LogVerbosityLevel`です。  
  
4.  設定、`LogVerbosityLevel`値を`1`します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)