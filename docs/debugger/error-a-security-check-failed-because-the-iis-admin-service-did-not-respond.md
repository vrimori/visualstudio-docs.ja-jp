---
title: "エラー: IIS 管理サービスが応答しなかったために、セキュリティ チェックが失敗しました |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 85b96d9e1396933519da71e93bac075ee51af001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>エラー ： IIS 管理サービスが応答しないため、セキュリティ チェックに失敗しました。
このエラーは、IIS Admin サービスが応答しないときに発生します。 これは通常、IIS のインストールに問題があることを意味します。 最初に、を使用して、サービスが実行されていることを確認、 **Services**ツールから**管理ツール**です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して IIS を再インストール、**プログラム追加と削除**コントロール パネルの します。  
  
-   - または -  
  
-   コントロール パネルの [アプリケーションの追加と削除] を使って、コンピューターから IIS を削除します。 IIS を削除しても問題が解決しない場合は、レジストリをチェックして、次のキーが存在しないことを確認します。  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     - または -  
  
-   コントロール パネルの [管理ツール] を使って、IIS Admin サービスを無効にします。 これによって、コンピューター上の IIS は無効になります。  
  
     この 3 つの手順のいずれかを実行した後は、コンピューターを再起動します。  
  
     詳細については、IIS のドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)