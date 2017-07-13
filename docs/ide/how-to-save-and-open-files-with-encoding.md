---
title: "方法 : エンコーディングを使用してファイルを保存および開く | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 83faa2ad32073c4133295953afa6259e88eee2d5
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---
# 方法 : エンコーディングを使用してファイルを保存および開く
<a id="how-to-save-and-open-files-with-encoding" class="xliff"></a>
双方向言語をサポートするために、特定の文字エンコーディングを使用してファイルを保存できます。 また、Visual Studio でファイルが正しく開かれるように、ファイルを開くときにもエンコーディングを指定できます。  
  
### エンコーディングを使用してファイルを保存するには
<a id="to-save-a-file-with-encoding" class="xliff"></a>  
  
1.  **[ファイル]** メニューの **[名前を付けてファイルを保存]** を選び、**[保存]** の横のドロップダウン ボタンをクリックします。  
  
     **[保存オプションの詳細設定]** ダイアログ ボックスが表示されます。  
  
2.  **[エンコード]** で、ファイルに使うエンコーディングを選択します。  
  
3.  必要に応じて、**[行の終わり]** で行末文字の書式を選びます。  
  
     このオプションは、異なるオペレーティング システムのユーザーとファイルを交換する場合に便利です。  
  
     特定の方法でエンコードされていることがわかっているファイルを使用する場合は、ファイルを開くときに、そのエンコーディングを使用するように指定できます。 その方法は、ファイルがプロジェクトの一部であるかどうかによって異なります。  
  
### プロジェクトの一部であるエンコードされたファイルを開くには
<a id="to-open-an-encoded-file-that-is-part-of-a-project" class="xliff"></a>  
  
1.  **ソリューション エクスプローラー**でファイルを右クリックし、**[ファイルを開くアプリケーションの選択]** を選びます。  
  
2.  **[ファイルを開くアプリケーションの選択]** ダイアログ ボックスで、ファイルを開くエディターを選びます。  
  
     フォーム エディターなど、多くの Visual Studio エディターは、エンコーディングを自動検出し、ファイルを適切に開きます。 エンコーディングを選択できるエディターの場合は、**[エンコード]** ダイアログ ボックスが表示されます。  
  
3.  **[エンコード]** ダイアログ ボックスで、エディターで使うエンコーディングを選びます。  
  
### プロジェクトの一部ではないエンコードされたファイルを開くには
<a id="to-open-an-encoded-file-that-is-not-part-of-a-project" class="xliff"></a>  
  
1.  **[ファイル]** メニューの **[開く]** をポイントし、**[ファイル]** または **[Web のファイル]** を選んで、開くファイルを選びます。  
  
2.  **[開く]** ボタンの横のドロップダウン ボタンをクリックし、**[ファイルを開くアプリケーションの選択]** を選びます。  
  
3.  前の手順の 2. と 3. を実行します。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [エンコード方式および Windows フォームのグローバリゼーション](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)
