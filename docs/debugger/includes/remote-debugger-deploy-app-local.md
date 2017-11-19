---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
1. **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**発行**(Web フォームの**Web アプリの発行**)。

2. **発行**ダイアログ ボックスで、**フォルダー**をクリックして**参照**、新しいフォルダーを作成し、 **C:\Publish**です。

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    アプリについては、Web フォームを選択して**カスタム**発行 ダイアログ ボックスで、プロファイル名を入力し、選択**OK**です。

3. **[発行]**をクリックします。

    Visual Studio では、フォルダーにプロジェクトを発行します。 出力ウィンドウに進行状況を示しています。

4. **発行**ダイアログ ボックスで、をクリックして、**設定**リンクをクリックして、**設定**タブです。

5. 構成を設定**デバッグ****すべての既存のファイルを発行する前に削除**、順にクリック**保存**です。

    > [!NOTE]
    > リリース ビルドを使用する場合を発行するときに、web.config ファイルでデバッグを無効にします。

6. **[発行]**をクリックします。

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    アプリケーションの発行、**デバッグ**ローカル フォルダーにプロジェクトの構成。

5. Visual Studio コンピューターからの ASP.NET プロジェクト ディレクトリを ASP.NET アプリ用に構成されたローカル ディレクトリにコピー (この例では**C:\Publish**) Windows Server コンピューターにします。 このチュートリアルでは、想定していますが、手動でコピーする、PowerShell、Xcopy、Robocopy などその他のツールを使用することができます。

    > [!CAUTION]
    >  コードまたは再構築に変更を加える必要がある場合は再パブリッシュする必要がありますしてこの手順を繰り返します。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。

6. Windows Server、お使いのブラウザーでアプリを開くことで、アプリが正しく実行できることを確認します。

    アプリが正常に動作しない場合がありますが一致しない、サーバーと、Visual Studio コンピューターにインストールされている ASP.NET のバージョン間か IIS または Web サイトの構成に問題があります。 前の手順を再確認します。