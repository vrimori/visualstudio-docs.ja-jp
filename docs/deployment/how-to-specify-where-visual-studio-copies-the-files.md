---
title: ファイルをコピーする場所の指定 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c2bdc2f2b7285e9d7bd29e17fec4b9be33fdff2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979739"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>方法: Visual Studio がファイルをコピーする場所を指定する
ClickOnce を使用してアプリケーションを発行する場合、`Publish Location` プロパティによってアプリケーション ファイルとマニフェストが配置される場所が指定されます。 これには、ファイル パスまたは FTP サーバーへのパスを指定できます。  
  
 **[プロジェクト デザイナー]** の **[発行]** ページで、または、発行ウィザードを使用して `Publish Location` プロパティを指定することができます。 詳細については、「[方法 :発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)」を参照してください。  
  
> [!NOTE]
>  ClickOnce を使用してアプリケーションの複数のバージョンをインストールすると、以前のバージョンのアプリケーションは、指定した発行場所の Archive というフォルダーに移されます。 以前のバージョンがこのようにアーカイブされることで、インストール ディレクトリが以前のバージョンのフォルダーから分離されます。  
  
### <a name="to-specify-a-publishing-location"></a>発行場所を指定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[発行]** タブをクリックします。  
  
3. **[発行場所]** フィールドに、次の形式のいずれかを使用して、発行場所を入力します。  
  
   - ファイル共有またはディスク パスを発行するには、UNC パス (*\\\Server\ApplicationName*) またはファイル パス (*C:\Deploy\ApplicationName*) のいずれかを使用して、パスを入力します。  
  
   - FTP サーバーを発行するには、<em>ftp://ftp.microsoft.com/\<アプリケーション名></em> という形式を使用して、パスを入力します。  
  
     **[発行場所]** ボックスでは、テキストは参照 **[...]** ボタンが機能する順番で並んでいる必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)