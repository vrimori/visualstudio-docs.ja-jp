---
title: 'エラー: IIS 管理サービスが応答しないために、セキュリティ チェックが失敗しました |。Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a90a684a9de45e1fba67460d0ba0f01554d248f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207195"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>エラー ： IIS 管理サービスが応答しないため、セキュリティ チェックに失敗しました。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このエラーは、IIS Admin サービスが応答しないときに発生します。 これは通常、IIS のインストールに問題があることを意味します。 最初に、を使用して、サービスが実行されていることを確認、**サービス**ツールから**管理ツール**します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して IIS を再インストール、**プログラム追加と削除**コントロール パネル。  
  
-   - または -  
  
-   コントロール パネルの [アプリケーションの追加と削除] を使って、コンピューターから IIS を削除します。 IIS を削除しても問題が解決しない場合は、レジストリをチェックして、次のキーが存在しないことを確認します。  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     - または -  
  
-   コントロール パネルの [管理ツール] を使って、IIS Admin サービスを無効にします。 これによって、コンピューター上の IIS は無効になります。  
  
     この 3 つの手順のいずれかを実行した後は、コンピューターを再起動します。  
  
     詳細については、IIS のドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



