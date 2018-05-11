---
title: '方法: Visual Studio がファイルをコピーする場所を指定して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b4e626253d9d07a9f263304d02739bdb3f4b012
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>方法: Visual Studio がファイルをコピーする場所を指定する
ClickOnce を使用してアプリケーションを発行する場合、`Publish Location` プロパティによってアプリケーション ファイルとマニフェストが配置される場所が指定されます。 これには、ファイル パスまたは FTP サーバーへのパスを指定できます。  
  
 指定することができます、`Publish Location`プロパティを**発行**のページ、**プロジェクト デザイナー**、または発行ウィザードを使用しています。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
> [!NOTE]
>  ClickOnce を使用してアプリケーションの複数のバージョンをインストールすると、以前のバージョンのアプリケーションは、指定した発行場所の Archive というフォルダーに移されます。 以前のバージョンがこのようにアーカイブされることで、インストール ディレクトリが以前のバージョンのフォルダーから分離されます。  
  
### <a name="to-specify-a-publishing-location"></a>発行場所を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **発行場所**フィールドに、次の形式のいずれかを使用して、発行場所を入力します。  
  
    -   ファイル共有またはディスク パスに発行する場合に、UNC パスを使用して、パスを入力 (\\\Server\ApplicationName) またはファイル パス (C:\Deploy\ApplicationName)。  
  
    -   FTP サーバーを発行するには、ftp://ftp.microsoft.com/ApplicationName という形式を使用して、パスを入力します。  
  
     テキスト内に存在する必要があります、**発行場所**ボックスの 参照の順序で (**.**) ボタンが機能します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)