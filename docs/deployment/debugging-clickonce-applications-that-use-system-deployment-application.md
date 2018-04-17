---
title: System.Deployment.Application を使用して ClickOnce アプリケーションのデバッグ |Microsoft ドキュメント
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
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e637a8abf3255605415067d02fb474503c3de4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開では、アプリケーションを更新する方法を構成することができます。 ただし、使用およびカスタマイズする必要がある場合は、高度な[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置機能によって提供される展開のオブジェクト モデルにアクセスする必要がある<xref:System.Deployment.Application>です。 使用することができます、<xref:System.Deployment.Application>高度なタスクをなどの Api:  
  
-   アプリケーションで「今すぐ更新」オプションを作成します。  
  
-   さまざまなアプリケーション コンポーネントの条件付きでオンデマンド ダウンロードします。  
  
-   更新プログラムをアプリケーションに直接統合  
  
-   クライアント アプリケーションが常に最新の状態を保証します。  
  
 <xref:System.Deployment.Application> Api の動作と、アプリケーションが配置されるときにのみ[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]テクノロジは、それらをデバッグする唯一の方法を使用して、アプリケーションを展開する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、それにアタッチし、それをデバッグします。 デバッガーをアタッチできないことが事前に、アプリケーションが起動するデバッガーをアタッチする前に実行する場合に多くの場合、このコードが実行されるためです。 解決方法では、更新プログラムの確認コードまたはオンデマンドでコードの前に改ページ (または Visual Basic プロジェクトでの位置) を配置します。  
  
 推奨されるデバッグ手法は次のとおりです。  
  
1.  開始する前に、シンボル (.pdb) とソース ファイルのアーカイブを確認します。  
  
2.  バージョン 1 のアプリケーションを展開します。  
  
3.  新しい空のソリューションを作成します。 **ファイル** メニューのをクリックして**新規**、し**プロジェクト**です。 **新しいプロジェクト** ダイアログ ボックスで、**その他のプロジェクトの種類** ノードを選択し、 **Visual Studio ソリューション**フォルダーです。 **テンプレート**ペインで、**空のソリューション**です。  
  
4.  この新しいソリューションのプロパティには、アーカイブ済みのソースの場所を追加します。 **ソリューション エクスプ ローラー**ソリューション ノードを右クリックし、**プロパティ**です。 **プロパティ ページ**ダイアログ ボックスで、**デバッグ ソース ファイル**、アーカイブ済みのソース コードのディレクトリを追加します。 それ以外の場合、デバッガーは、最新でないソース ファイルを検索、ソース ファイルのパスが .pdb ファイルに記録されるためです。 デバッガーは、古いソース ファイルを使用している場合、ソースが一致しないことを示すメッセージを参照してください。  
  
5.  デバッガーが .pdb ファイルを検索することを確認します。 アプリでそれらを配置した場合、デバッガーにより自動的に検索します。 常には、アセンブリの横にある問題の最初にあります。 それ以外の場合、アーカイブのパスを追加する必要が、**シンボル (.pdb) ファイルの場所**(からこのオプションにアクセスする、**ツール** メニューのをクリックして**オプション**、を開く**デバッグ**ノード、およびクリック**シンボル**)。  
  
6.  デバッグの間での動作、`CheckForUpdate`と`Download` / `Update`メソッドの呼び出しです。  
  
     たとえば、更新プログラムのコードはようになります可能性があります。  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  バージョン 2 を展開します。  
  
8.  バージョン 2 の更新プログラムをダウンロードしながら、バージョン 1 のアプリケーションにデバッガーをアタッチしようとしてください。 またはを使用して、`System.Diagnostics.Debugger.Break`メソッドまたは単に`Stop`Visual Basic でします。 もちろん、実稼働コードでいないこれらのメソッド呼び出しのままにする必要があります。  
  
     たとえば、Windows フォーム アプリケーションを開発しており、内の更新ロジックでこのメソッドのイベント ハンドラーを設定するとします。 これをデバッグするに取り付けるだけで、ボタンが押された、ブレークポイントを設定する前に (適切なアーカイブ ファイルを開くし、そこでブレークポイントを設定ことを確認ください)。  
  
 使用して、<xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>プロパティを呼び出す、 <xref:System.Deployment.Application> Api アプリケーションが展開される場合にのみ; Api 呼び出さないでくださいでのデバッグ中に[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application>