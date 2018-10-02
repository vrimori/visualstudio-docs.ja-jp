---
title: '方法: ビジュアライザーをインストール |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5152c47635f8ca2f2bb0a6a32c7767682006860a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548783"
---
# <a name="how-to-install-a-visualizer"></a>方法 : ビジュアライザーをインストールする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ビジュアライザーをインストール](https://docs.microsoft.com/visualstudio/debugger/how-to-install-a-visualizer)します。  
  
作成したビジュアライザーは、インストールして初めて [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で使用できるようになります。 ビジュアライザーのインストールは簡単です。  
  
> [!NOTE]
>  **ストア**アプリ、標準のテキストのみ HTML、XML、および JSON ビジュアライザーがサポートされています。 カスタム (ユーザーが作成した) ビジュアライザーはサポートされていません。  
  
### <a name="to-install-a-visualizer"></a>ビジュアライザーをインストールするには  
  
1.  作成したビジュアライザーを含むダイナミック リンク ライブラリ (DLL: Dynamic Link Library) を探します。  
  
2.  DLL を次のいずれかの場所にコピーします。  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  マネージド ビジュアライザーをリモート デバッグで使用するには、DLL をリモート コンピューター上の同じパスにコピーします。  
  
4.  デバッグ セッションを再開します。  
  
## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [方法 : ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)



