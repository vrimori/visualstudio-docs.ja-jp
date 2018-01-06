---
title: "方法: ARM デバイスでグラフィックス診断を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eedc7e454c6523c1ab29e4ae685b14954c8e6d98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>方法: ARM デバイスでグラフィックス診断を使用する
グラフィックス診断は、Windows RT 8.1 または Windows Phone 8.1 を実行する ARM ベースのデバイスで Direct3D アプリケーションのリモート デバッグをサポートします。 Direct3D がデバイス上で実行されている間に、Direct3D アプリケーショングラフィックス情報をキャプチャできます。また以前にキャプチャしたグラフィックス情報については、デバイスを再生コンピューターとして使用できます。  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>ARM ベースのデバイスでのグラフィックス診断の使用  
 Visual Studio は ARM ベースのデバイス上では稼動しないため、これらのデバイス上で稼動するアプリケーションを分析するにはリモート デバッガーを使用する必要があります。 リモート デバッガーはグラフィックスのキャプチャと再生をサポートしているため、アプリケーションをデバッグするのと同じくらい簡単に、レンダリングのエラーを診断し、これらのデバイスのグラフィックス パフォーマンスを評価することができます。  
  
 グラフィックス診断の機能を使用するには、最初にデバイス上でリモート デバッギングを有効にします。  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>ARM ベースのデバイス上でリモート デバッギングを有効にするには  
  
1.  インストール、 [ARM Kits Policy](http://msdn.microsoft.com/windows/desktop/dn469188) ARM ベースのデバイスにします。  
  
2.  インストール、 [Remote Debugging Tools](http://go.microsoft.com/fwlink/?LinkId=393086) ARM ベースのデバイスにします。  
  
> [!IMPORTANT]
>  Windows Phone 8.1 のデバイスの場合は、開発用にスマートフォンを登録しなければならないことがあります。 そのためには、自身が登録されている開発者であることが必要です。 詳細については、次を参照してください。[展開および Windows Phone 8 のアプリを実行する方法](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx)です。  
  
 デバイス上でリモート デバッギングを有効にしたら、デバイスをデバッグ ターゲットにしてグラフィックス診断を開始します。  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>デバイス上でグラフィックス診断を構成および開始するには  
  
1.  **ソリューション プラットフォーム**ドロップダウン リストで、 **ARM** ARM ベースのデバイスをリモート デバッギング ターゲットとして使用できるようにします。  
  
2.  **デバッグ ターゲット**ドロップダウン リストで、ARM デバイスを選択します。  
  
3.  メニューで、次のように選択します。**デバッグ**、**グラフィックス**、**診断の開始**です。 (キーボード: Alt + F5)  
  
## <a name="see-also"></a>参照  
 [リモート コンピューターでの UWP アプリを実行します。](../run-windows-store-apps-on-a-remote-machine.md)   
 [方法: グラフィックス診断再生マシンを変更する](how-to-change-the-graphics-diagnostics-playback-machine.md)