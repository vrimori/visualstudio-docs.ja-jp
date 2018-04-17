---
title: '方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール |Microsoft ドキュメント'
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
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6f1d71d9bbabeb5e912ba01cf6237ddd94d00b3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>方法 : ClickOnce アプリケーションと共に必須コンポーネントをインストールする
すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションで実行する前に、.NET Framework の正しいバージョンがコンピューターにインストールされているが必要です。 多くのアプリケーションにもその他の前提条件です。 発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、アプリと一緒にパッケージ化する前提条件コンポーネントのセットを選択することができます。 インストール時に、チェックされます。 それぞれの前提条件のかどうかは、既に存在します。 を決定するにはインストールする前にインストールされていない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
 パッケージ化および前提条件を発行、代わりに、コンポーネントのダウンロード場所も指定できます。 たとえばを発行するすべてのアプリケーションと共に必須コンポーネントを含むではなくことができます、一元的なファイル共有または Web 上の場所を含むすべての前提条件のインストーラー: コンポーネントのダウンロード、インストール時とその場所からインストールします。  
  
> [!IMPORTANT]
>  最初に発行する前に、開発用コンピューターに前提条件インストーラー パッケージを追加する必要があります[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 詳細については、次を参照してください。[する方法: ClickOnce アプリケーションと共に必須コンポーネントを含める](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)です。  
  
 前提条件で管理、**の前提条件**ダイアログ ボックスからアクセスできる、**発行**のペイン、**プロジェクト デザイナー**です。  
  
> [!NOTE]
>  だけでなく、事前に定義された前提条件の一覧、一覧に、独自のコンポーネントを追加できます。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)です。  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>ClickOnce アプリケーションと共にインストールする前提条件を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  選択、**発行**ウィンドウです。  
  
3.  をクリックして、**の前提条件**を開く ボタン、**の前提条件** ダイアログ ボックス。  
  
4.  **[必須コンポーネント]** ダイアログ ボックスの **[必須コンポーネントをインストールするセットアップ プログラムを作成する]** チェック ボックスをオンにします。  
  
5.  **の前提条件**一覧で、コンポーネントをインストールし、をクリックすることを確認して**OK**です。  
  
     選択したコンポーネントをパッケージ化し、アプリケーションと共に発行されます。  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>前提条件を別のダウンロード場所を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  選択、**発行**ウィンドウです。  
  
3.  をクリックして、**の前提条件**を開く ボタン、**の前提条件** ダイアログ ボックス。  
  
4.  **[必須コンポーネント]** ダイアログ ボックスの **[必須コンポーネントをインストールするセットアップ プログラムを作成する]** チェック ボックスをオンにします。  
  
5.  **の前提条件のインストール場所を指定**セクションで、**次の場所から必須コンポーネントをダウンロード**です。  
  
6.  ドロップダウン リストから場所を選択または URL、ファイル パスまたは FTP の場所を入力し、クリックして**[ok] です。**  
  
    > [!NOTE]
    >  指定した位置に指定されたコンポーネントのインストーラーが存在することを確認する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)