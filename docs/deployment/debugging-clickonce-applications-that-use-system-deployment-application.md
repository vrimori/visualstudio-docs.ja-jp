---
title: System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ |Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6addfb72ae1e67b846433c9762163138523df68
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872412"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開を使用するアプリケーションを更新する方法を構成できます。 ただし、使用およびカスタマイズする必要がある場合は、高度な[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開の機能によって提供される展開オブジェクト モデルにアクセスする必要がある<xref:System.Deployment.Application>します。 使用することができます、<xref:System.Deployment.Application>高度なタスクをなどの Api:  
  
- アプリケーションで「今すぐ更新」オプションを作成します。  
  
- さまざまなアプリケーション コンポーネントの条件付きでオンデマンド ダウンロードします。  
  
- 更新プログラム、アプリケーションに直接統合されています  
  
- クライアント アプリケーションが常に最新であることを保証  
  
  <xref:System.Deployment.Application> Api 動作とアプリケーションが配置されるときにのみ[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を使用して、アプリケーションをデプロイするテクノロジ、それらをデバッグする唯一の方法は[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、それにアタッチし、それをデバッグします。 デバッガーをアタッチすることは難しい、アプリケーションが起動して、デバッガーをアタッチする前に実行時に多くの場合、このコードを実行しているので、事前します。 ソリューションは、前に、更新プログラムの確認コードまたはオンデマンドでコードが中断 (または Visual Basic プロジェクトの停止) を配置します。  
  
  推奨されるデバッグ手法は次のとおりです。  
  
1. 開始する前に、シンボル (.pdb) とソース ファイルのアーカイブを確認します。  
  
2. アプリケーションのバージョン 1 を展開します。  
  
3. 新しい空のソリューションを作成します。 **ファイル** メニューのをクリックして**新規**、し**プロジェクト**します。 **新しいプロジェクト** ダイアログ ボックスで、**その他のプロジェクトの種類**ノードを選択し、 **Visual Studio ソリューション**フォルダー。 **テンプレート**ペインで、**空のソリューション**します。  
  
4. この新しいソリューションのプロパティには、アーカイブされたソースの場所を追加します。 **ソリューション エクスプ ローラー**ソリューション ノードを右クリックし、クリックして**プロパティ**します。 **プロパティ ページ**ダイアログ ボックスで、**デバッグ ソース ファイル**、アーカイブ済みのソース コードのディレクトリを追加します。 それ以外の場合、ソース ファイルのパスが .pdb ファイルに記録されるため、デバッガーは、古くなっているソース ファイルが見つけされます。 デバッガーは、古くなっているソース ファイルを使用している場合、ソースが一致しないことを知らせるメッセージを参照してください。  
  
5. デバッガーが検出できるように、 *.pdb*ファイル。 アプリケーションでそれらをデプロイした場合、デバッガーにより自動的に検索します。 常に、アセンブリの横にある問題は最初を検索します。 それ以外の場合、アーカイブのパスを追加する必要がありますには、**シンボル (.pdb) ファイルの場所**(から、このオプションにアクセスする、**ツール** メニューのをクリックして**オプション**、開き、 **デバッグ**ノード、およびクリック**シンボル**)。  
  
6. デバッグの間での動作、`CheckForUpdate`と`Download` / `Update`メソッドの呼び出し。  
  
    たとえば、更新プログラムのコードはようになります可能性があります。  
  
   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. バージョン 2 を展開します。  
  
8. バージョン 2 更新プログラムをダウンロードしながら、バージョン 1 のアプリケーションにデバッガーをアタッチしようとしてください。 またはを使用して、`System.Diagnostics.Debugger.Break`メソッドまたは単に`Stop`Visual Basic でします。 もちろん、実稼働コードでいないこれらのメソッド呼び出しのままにする必要があります。  
  
    たとえば、Windows フォーム アプリケーションを開発することで更新ロジックは、このメソッドのイベント ハンドラーがある想定をしています。 これをデバッグする単にアタッチ、ボタンが押された、ブレークポイントを設定する前に (適切なアーカイブ ファイルを開くし、そこにブレークポイントを設定することを確認してください)。  
  
   使用して、<xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>プロパティを呼び出す、<xref:System.Deployment.Application>でのデバッグ中にアプリケーションが展開されている場合にのみ Api は、Api を起動する必要がありますいない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application>