---
title: 'チュートリアル: 再署名が不要で商標を保持する ClickOnce アプリケーションを手動で展開する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0584aac376345bc508e5f2088decd45b8c64783b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>チュートリアル : 再署名が不要で商標を保持する ClickOnce アプリケーションの手動配置
作成するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションと、それを公開する顧客に渡すと展開、顧客が従来から配置マニフェストを更新して再署名する必要があります。 ほとんどの場合に推奨される方法は引き続き、中に、.NET Framework 3.5 を作成できます[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]顧客して、新しい配置マニフェストを再生成することがなく展開することを展開します。 詳細については、次を参照してください。 [ClickOnce アプリケーションのテスト用の展開および Resigning なしの実稼働サーバー](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)です。  
  
 作成するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションと、それを公開する顧客に渡すと展開、アプリケーション、顧客のブランド化を使用できるまたはブランド化を保持することができます。 たとえば、アプリケーションが 1 つの専用アプリケーションの場合は、可能性があります残しておきたいブランド化します。 アプリケーションは、顧客ごとにカスタマイズされた高場合、は、お客様のブランド化を使用することができます。 .NET Framework 3.5 は、組織に展開するアプリケーションに付与すると、ブランド化を保持すること、発行者情報、およびセキュリティの署名を使用できます。 詳細については、次を参照してください。 [ClickOnce アプリケーションの作成の他のユーザーのデプロイに](../deployment/creating-clickonce-applications-for-others-to-deploy.md)です。  
  
> [!NOTE]
>  このチュートリアルで展開手動で作成するコマンド ライン ツールの Mage.exe または MageUI.exe のグラフィック ツールを使用しています。 手動による展開の詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルの手順を実行するには、次のものが必要。  
  
-   Windows フォーム アプリケーションを展開する準備ができたらです。 このアプリケーションは、WindowsFormsApp1 として参照されます。  
  
-   Visual Studio または Windows SDK。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>複数の展開とブランド化のサポートが Mage.exe を使用して ClickOnce アプリケーションを展開するには  
  
1.  Visual Studio コマンド プロンプトを開き、または[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]コマンド プロンプト、および格納するディレクトリへの変更、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ファイル。  
  
2.  配置の現在のバージョンにちなんだ名前のディレクトリを作成します。 これが初めてアプリケーションを展開することである場合は、おそらくを選択します**1.0.0.0**です。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる可能性があります。  
  
3.  という名前のサブディレクトリを作成する**bin**し、実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、すべてのアプリケーション ファイルをコピーします。  
  
4.  Mage.exe への呼び出しを使用してアプリケーション マニフェストを生成します。  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  デジタル証明書を使用してアプリケーション マニフェストに署名します。  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Mage.exe への呼び出しで配置マニフェストを生成します。 既定では、Mage.exe ではマーク、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]が実行できるようにする両方オンラインとオフラインのインストールされているアプリケーションとして展開します。 アプリケーション使用できるようにする、ユーザーがオンラインのときにのみ、使用、`-i`引数の値を持つ`f`します。 このアプリケーションは、複数の展開機能を利用するための除外、 `-providerUrl` Mage.exe に渡す引数。 (を除くより前のバージョン 3.5、.NET Framework のバージョンで`-providerUrl`のオフラインのアプリケーションが、エラーになります)。  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  配置マニフェストに署名しません。  
  
8.  すべてのファイルをネットワーク上のアプリケーションを展開すると、顧客に提供します。  
  
9. この時点では、お客様は、自分の自動生成された証明書で配置マニフェストをサインインする必要があります。 たとえば、お客様の会社 Adventure Works という名前の場合は、MakeCert.exe ツールを使用して自己署名証明書を生成彼できます。 次に、Mage.exe を渡すことができる、PFX ファイルに、MakeCert.exe によって作成されたファイルを結合するのに Pvk2pfx.exe ツールを使用します。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. お客様は、配置マニフェストの署名を次にこの証明書を使用します。  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. お客様は、ユーザーにアプリケーションを展開します。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>複数の展開とブランド化のサポートが MageUI.exe を使用して ClickOnce アプリケーションを展開するには  
  
1.  Visual Studio コマンド プロンプトを開き、または[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]コマンド プロンプト、および格納するディレクトリに移動、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ファイル。  
  
2.  という名前のサブディレクトリを作成する**bin**し、実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、すべてのアプリケーション ファイルをコピーします。  
  
3.  配置の現在のバージョンにちなんだ名前のサブディレクトリを作成します。 これが初めてアプリケーションを展開することである場合は、おそらくを選択します**1.0.0.0**です。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる可能性があります。  
  
4.  移動、 \\ **bin**手順 2. で作成したディレクトリにディレクトリ。  
  
5.  MageUI.exe のグラフィック ツールを起動します。  
  
    ```  
    MageUI.exe  
    ```  
  
6.  選択して、新しいアプリケーション マニフェストを作成する**ファイル**、**新規**、 **Application Manifest**  メニューからです。  
  
7.  既定の**名前** タブで、この展開の名前とバージョン番号を入力します。 またの値を指定**パブリッシャー**を展開すると、[スタート] メニューで、アプリケーションのショートカット リンクのフォルダー名として使用されます。  
  
8.  選択、**アプリケーション オプション** タブでをクリックし、**信頼情報を使用してアプリケーション マニフェスト**です。 これにより、このサード パーティ製のブランド化[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
9. 選択、**ファイル** タブでをクリックし、**参照**アプリケーション ディレクトリ ボックスの横にあるボタンをクリックします。  
  
10. 手順 2. で作成したアプリケーション ファイルを含んでいるディレクトリを選択し、をクリックして**OK**フォルダーの選択 ダイアログ ボックスでします。  
  
11. をクリックして、 **Populate**ファイル リストに、すべてのアプリケーション ファイルを追加するボタンをクリックします。 アプリケーションに 1 つ以上の実行可能ファイルが含まれている場合は、スタートアップ アプリケーションとしてこの展開のメインの実行可能ファイルをマーク を選択して**エントリ ポイント**から、**ファイルの種類**ドロップダウン リスト。 (場合は、アプリケーションには、1 つの実行可能ファイルのみが含まれる、MageUI.exe は対象として設定する。)  
  
12. 選択、**必要なアクセス許可**タブし、信頼をアサートするアプリケーションを作成する必要がありますのレベルを選択します。 既定値は**完全信頼**、ほとんどのアプリケーションに適したされます。  
  
13. 選択**ファイル**、**保存**メニューのおよびアプリケーション マニフェストを保存します。 保存すると、アプリケーション マニフェストに署名するように促されます。  
  
14. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルと符号**し、省略記号ボタンを使用して、ファイル システムからの証明書の選択 (**.**) ボタンをクリックします。  
  
     - または -  
  
     証明書がコンピューターからアクセス可能な証明書ストアに保持されている場合は、選択、 **stored certificate オプションを使用してサインイン**、表示された一覧から証明書を選択します。  
  
15. 選択**ファイル**、**新規**、**配置マニフェストは**、配置マニフェストを作成するのには、メニューから、次に、**名前** タブで、指定、名前とバージョン番号 (**1.0.0.0**この例では)。  
  
16. 切り替えて、**更新**タブをクリックし、このアプリケーションを更新する頻度を指定します。 アプリケーションで使用する場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Deployment API 自体は、更新プログラムのチェックをオフにチェック ボックスをオン**アプリケーションの更新プログラムを確認する必要があります**です。  
  
17. 切り替えて、**アプリケーション参照**タブです。をクリックして、すべての値をこのタブで事前設定できる、 **マニフェスト**前の手順で作成したボタンをクリックし、アプリケーション マニフェストを選択します。  
  
18. 選択**保存**し、配置マニフェストをディスクに保存します。 保存すると、アプリケーション マニフェストに署名するように促されます。 をクリックして**キャンセル**を署名なし、マニフェストを保存します。  
  
19. すべてのアプリケーション ファイルを顧客に提供します。  
  
20. この時点では、お客様は、自分の自動生成された証明書で配置マニフェストをサインインする必要があります。 たとえば、お客様の会社 Adventure Works という名前の場合は、MakeCert.exe ツールを使用して自己署名証明書を生成彼できます。 次に、Pvk2pfx.exe ツールを使用して、MageUI.exe に渡すことができる、PFX ファイルに、MakeCert.exe によって作成されたファイルを結合します。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 生成された証明書が、お客様はようになりました MageUI.exe で配置マニフェストを開き、保存して、配置マニフェストを署名します。 署名のダイアログ ボックスが表示されたら、選択**証明書ファイルと符号**オプションと彼は、ディスクに保存 PFX ファイルを選択します。  
  
22. お客様は、ユーザーにアプリケーションを展開します。  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)