---
title: '方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e363b021f8dfb82aa641a1baac4d2f33e0bd3d2e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152475"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールします。
すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、実行する前に、.NET Framework の正しいバージョンがコンピューターにインストールされている必要があります。 多くのアプリケーションもその他の前提条件があります。 発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、アプリケーションと共にパッケージ化する前提条件コンポーネントのセットを選択できます。 かどうかは既に存在するかを判断する各前提条件のインストール時に、チェックが実行されます。インストールする前にインストールされていない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
 パッケージ化と発行の前提条件ではなく、コンポーネントのダウンロード場所を指定することもできます。 たとえば、発行されたすべてのアプリケーションと共に必須コンポーネントを含むではなく可能性がありますを使用する一元的なファイル共有またはすべての前提条件インストーラーを含む Web 上の場所: コンポーネントのダウンロード、インストール時に、その場所からインストールします。  
  
> [!IMPORTANT]
>  初めて発行する前に、開発用コンピューターに必須コンポーネントのインストーラー パッケージを追加する必要があります[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 詳細については、次を参照してください。[方法: ClickOnce アプリケーションと共に必須コンポーネントを含める](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)します。  
  
 前提条件がで管理されている、**の前提条件**からアクセスできるダイアログ ボックス、**発行**のウィンドウ、**プロジェクト デザイナー**。  
  
> [!NOTE]
>  前提条件の定義済みの一覧だけでなく、一覧に、独自のコンポーネントを追加できます。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)します。  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>ClickOnce アプリケーションと共にをインストールする前提条件を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  選択、**発行**ウィンドウ。  
  
3.  をクリックして、**の前提条件**ボタンをクリックする、**の前提条件** ダイアログ ボックス。  
  
4.  **[必須コンポーネント]** ダイアログ ボックスの **[必須コンポーネントをインストールするセットアップ プログラムを作成する]** チェック ボックスをオンにします。  
  
5.  **の前提条件**一覧で、インストール、およびクリックするコンポーネントをチェックして**OK**します。  
  
     選択したコンポーネントをパッケージ化され、アプリケーションと共に発行されます。  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>前提条件の別のダウンロード場所を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  選択、**発行**ウィンドウ。  
  
3.  をクリックして、**の前提条件**ボタンをクリックする、**の前提条件** ダイアログ ボックス。  
  
4.  **[必須コンポーネント]** ダイアログ ボックスの **[必須コンポーネントをインストールするセットアップ プログラムを作成する]** チェック ボックスをオンにします。  
  
5.  **の前提条件のインストール場所を指定**セクションで、**次の場所から必須コンポーネントをダウンロード**します。  
  
6.  ボックスの一覧から場所を選択または URL、ファイルのパスまたは FTP の場所を入力し、クリックして**ok をクリックします。**  
  
    > [!NOTE]
    >  指定した位置に、指定したコンポーネントのインストーラーが存在することを確認する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)