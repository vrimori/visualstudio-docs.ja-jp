---
title: '方法: ClickOnce 配置エラー用のカスタム ログ ファイルの場所の設定 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647eed5145d9d80f9fc62249763726a5940a7345
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565719"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>方法 : ClickOnce 配置エラー用にカスタム ログ ファイルの場所を設定する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] すべての展開のログ ファイルのアクティブ化を保持します。 これらのログ記録のインストールと初期化に関連するすべてのエラー、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 既定では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]各展開のライセンス認証のための 1 つのログ ファイルを作成します。 インターネット一時ファイル フォルダーに、これらのログ ファイルを格納します。 アクティベーション エラーが発生し、ユーザーがクリックしたときに、展開のログ ファイルが、ユーザーに表示される**詳細**結果のエラー ダイアログ ボックス。  
  
 レジストリ エディターを使用して、特定のクライアントのこの動作を変更することができます (**regedit.exe**) をカスタム ログ ファイルのパスを設定します。 この場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を単一のファイルのすべての展開のライセンス認証の成功と失敗をログに記録します。  
  
> [!CAUTION]
>  レジストリ エディターを誤って使用する場合は、オペレーティング システムを再インストールする必要があります深刻な問題が発生する可能性があります。 問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
> [!NOTE]
>  切り捨てるか大きくなりすぎないようにするには、場合によっては、ログ ファイルを削除する必要があります。  
  
 次の手順では、1 つのクライアントのカスタム ログ ファイルの場所を設定する方法について説明します。  
  
### <a name="to-set-a-custom-log-file-location"></a>カスタム ログ ファイルの場所を設定するには  
  
1.  開いている**Regedit.exe**です。  
  
2.  ノードに移動`HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`です。  
  
3.  文字列値を設定`LogFilePath`完全なパスと、任意のカスタム ログの場所のファイル名にします。  
  
     この場所は、ユーザーが書き込みアクセスしているディレクトリにする必要があります。 たとえば、Windows Vista で、次のフォルダー構造を作成し、設定`LogFilePath`C:\Users に\\< ユーザー名\>\Documents\Logs\ClickOnce\installation.log です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)