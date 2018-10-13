---
title: '方法: ASP.NET アプリケーションのデバッグを有効にする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9d0e7a4b6f6daf4fb93884e6d5673ce550259ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235938"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>方法:ASP.NET アプリケーションのデバッグを有効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

デバッグを有効にするには、 **プロジェクト プロパティ** ページとアプリケーションの web.config ファイルの両方で有効にする必要があります。  
  
> [!NOTE]  
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Visual Basic または C# のプロジェクト プロパティで ASP.NET デバッグを有効にするには  
  
1.  **ソリューション エクスプローラー**で、Web プロジェクト名を右クリックし、 **[プロパティ]** をクリックします。  
  
2.  プロジェクトのプロパティ ページで、 **[Web]** タブをクリックします。  
  
3.  **[デバッガー]** の下で、 **[ASP.NET]** チェック ボックスをオンにします。  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>web.config ファイルでデバッグを有効にするには  
  
1.  標準のテキスト エディターまたは XML パーサーで web.config ファイルを開きます。  
  
    > [!NOTE]  
    > ただし、Web ブラウザーを使用してファイルにリモート アクセスすることはできません。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] では、セキュリティ上の理由から、ブラウザーが直接 Web.config ファイルにアクセスできないように Microsoft IIS を設定しています。 ブラウザーで構成ファイルにアクセスしようとすると、HTTP アクセス エラー 403 (禁止) が表示されます。  
  
2.  Web.config は XML ファイルなので、タグでマークされた入れ子のセクションが含まれます。 `configuration/system.web/compilation` 要素を探します。 compilation 要素が存在しない場合は、その要素を作成します。  
  
3.  `compilation` 要素内に `debug` 属性がない場合は、その属性を要素に追加します。  
  
4.  `debug` 属性の値が `true` に設定されていることを確認します。  
  
web.config ファイルは次の例のようになります。 場合によって configuration 要素と system.web 要素との間には次のセクションがあることに注意してください。  
  
-   configuration 要素と system.web 要素との間の element セクション。  
  
-   system.web 要素と compilation 要素との間の element セクション。  
  
-   compilation 要素には他の属性と要素が含まれる場合があります。  
  
## <a name="example"></a>例  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
Web.config ファイルが変更されると、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] が自動的に変更を検出し、新しい構成設定を適用します。 変更を反映させるためにコンピューターまたは IIS サーバーを再起動する必要はありません。  
  
Web サイトには、複数の仮想ディレクトリとサブディレクトリを含めることができ、それぞれに Web.config ファイルを用意できます。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションは、URL パスの上位レベルにある Web.config ファイルの設定を継承します。 階層構造の構成ファイルを利用して、下位の階層にあるすべてのアプリケーションなど、複数の [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションの設定を同時に変更できます。 ただし、階層内の下位のファイルで `debug` が設定されると、上位の値がオーバーライドされます。  
  
たとえば、www.microsoft.com/aaa/Web.config で `debug="true"` と指定すると、aaa フォルダーまたは aaa フォルダーのサブフォルダーにあるすべてのアプリケーションに、この設定が継承されます。 そのため、www.microsoft.com/aaa/bbb フォルダーにある [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションは、この設定を継承し、www.microsoft.com/aaa/ccc、www.microsoft.com/aaa/ddd などのフォルダーにあるすべての [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションもこの設定を継承します。 唯一の例外は、アプリケーションの 1 つが、より低いレベルにある独自の Web.config ファイルで設定をオーバーライドする場合です。  
  
デバッグ モードを有効にすると、 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションのパフォーマンスに大きく影響します。 リリース バージョンのアプリケーションを配置したり、パフォーマンスの測定を実施したりする前には、デバッグ モードを無効にしてください。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)  
  




