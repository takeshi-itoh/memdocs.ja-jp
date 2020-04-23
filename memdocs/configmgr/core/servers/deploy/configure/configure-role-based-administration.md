---
title: ロール ベース管理の構成
titleSuffix: Configuration Manager
ms.date: 11/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-core
ms.topic: conceptual
ms.assetid: 57413dd3-b2f8-4a5f-b27f-8464d357caff
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 9f85f55e3bf982a75b27f65cd52c846f6a02f03f
ms.sourcegitcommit: bbf820c35414bf2cba356f30fe047c1a34c5384d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81704690"
---
# <a name="configure-role-based-administration-for-configuration-manager"></a>Configuration Manager に対してロール ベース管理を構成する

*適用対象:Configuration Manager (Current Branch)*

Configuration Manager のロール ベース管理では、セキュリティ ロール、セキュリティ スコープ、および割り当てられたコレクションを組み合わせて、各管理ユーザーの管理スコープを定義します。 管理スコープには、Configuration Manager コンソールで管理ユーザーが表示できるオブジェクト、および管理ユーザーが実行するアクセス許可を持っている、それらのオブジェクトに関連するタスクが含まれます。 役割に基づいた管理の構成は、階層内の各サイトに適用されます。  

 ロール ベース管理にまだ慣れていない場合は、「[ロール ベース管理の基礎](../../../understand/fundamentals-of-role-based-administration.md)」を参照してください。  

 ロール ベース管理および関連するセキュリティ設定を構成するときに、次の情報を参考にしてください。  

- [カスタム セキュリティ ロールの作成](#BKMK_CreateSecRole)  
- [セキュリティ ロールの構成](#BKMK_ConfigSecRole)  
- [オブジェクトのセキュリティ スコープの構成](#BKMK_ConfigSecScope)  
- [セキュリティを管理するコレクションの構成](#BKMK_ConfigColl)  
- [新しい管理ユーザーの作成](#BKMK_Create_AdminUser)  
- [管理ユーザーの管理スコープの変更](#BKMK_ModAdminUser)  

## <a name="create-custom-security-roles"></a><a name="BKMK_CreateSecRole"></a> カスタム セキュリティ ロールの作成

 Configuration Manager は、さまざまな組み込みのセキュリティ ロールを提供します。 追加のセキュリティ ロールが必要な場合、既存のセキュリティ ロールのコピーを作成し、このコピーを変更して、カスタム セキュリティ ロールを作成できます。 カスタム セキュリティ ロールを作成して、現在割り当てられているセキュリティ ロールには含まれていない、必要な追加のセキュリティ アクセス許可を管理ユーザーに付与できます。 カスタム セキュリティ ロールを使用すると、必要なアクセス許可のみ管理者に付与できるため、必要以上のアクセス許可を付与するセキュリティ ロールが割り当てられることがありません。  

 既存のセキュリティ ロールをテンプレートとして使用して新しいセキュリティ ロールを作成するには、次の手順に従います。  

### <a name="to-create-custom-security-roles"></a>カスタム セキュリティ ロールを作成するには

1. Configuration Manager コンソールで、 **[管理]** に移動します。  

2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[セキュリティ ロール]** を選択します。  

   次の手順のいずれかを使用して、新しいセキュリティ ロールを作成します。  

    - 新しいカスタム セキュリティ ロールを作成するには、次の操作を実行します。  

      1. 既存のセキュリティ ロールを選択し、新しいセキュリティ ロールのソースとして使用します。
      2. **[ホーム]** タブの **[セキュリティ ロール]** グループで、 **[コピー]** を選択します。 このアクションにより、ソース セキュリティ ロールのコピーが作成されます。  
      3. セキュリティ ロールのコピー ウィザードで、新しいカスタム セキュリティ ロールの **[名前]** を指定します。  
      4. **[セキュリティ操作の割り当て]** で、各 **[セキュリティ操作]** ノードを展開して使用可能なアクションを表示します。  
      5. セキュリティ操作の設定を変更するには、 **[値]** 列で下向きの矢印を選択し、 **[はい]** または **[いいえ]** を選択します。

            > [!CAUTION]  
            > カスタム セキュリティ ロールを構成する場合、新しいセキュリティ ロールに関連付けられる管理ユーザーが必要としないアクセス許可は付与しないようにしてください。 たとえば、**セキュリティ ロール** セキュリティ操作の値を **[変更]** にすると、そのセキュリティ ロールに関連付けられていなくても、すべてのアクセス可能なセキュリティ ロールを編集できるアクセス許可が管理ユーザーに付与されます。  

      6. アクセス許可を構成したら、 **[OK]** を選択して新しいセキュリティ ロールを保存します。  

    - 別の Configuration Manager 階層からエクスポートされたセキュリティ ロールをインポートするには、次の操作を実行します。  

        1. **[ホーム]** タブの **[作成]** グループで **[セキュリティ ロールのインポート]** を選択します。  
        2. インポートするセキュリティ ロールの構成を含む .xml ファイルを指定します。 **[開く]** を選択して手順を完了し、セキュリティ ロールを保存します。  

            > [!NOTE]  
            > セキュリティ ロールをインポートした後で、セキュリティ ロールのプロパティを編集して、そのセキュリティ ロールに関連付けられているオブジェクトのアクセス許可を変更できます。  

## <a name="configure-security-roles"></a><a name="BKMK_ConfigSecRole"></a> セキュリティ ロールの構成

 セキュリティ ロールに定義されているセキュリティ アクセス許可のグループは、セキュリティ操作の割り当てと呼ばれます。 セキュリティ操作の割り当ては、オブジェクトの種類と、各オブジェクトの種類で実行できる操作の組み合わせを表します。 カスタム セキュリティ ロールで実行できるセキュリティ操作を変更することはできますが、Configuration Manager で提供される組み込みのセキュリティ ロールを変更することはできません。  

 セキュリティ ロールのセキュリティ操作を変更するには、次の手順に従います。  

### <a name="to-modify-security-roles"></a>セキュリティ ロールを変更するには

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[セキュリティ ロール]** を選択します。  
3. 変更するカスタム セキュリティ ロールを選択します。  
4. **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** を選択します。  
5. **[アクセス許可]** タブを選択します。  
6. **[セキュリティ操作の割り当て]** で、各 **[セキュリティ操作]** ノードを展開して使用可能なアクションを表示します。  
7. セキュリティ操作の設定を変更するには、 **[値]** 列で下向きの矢印を選択し、 **[はい]** または **[いいえ]** を選択します。  

    > [!CAUTION]  
    > カスタム セキュリティ ロールを構成する場合、新しいセキュリティ ロールに関連付けられる管理ユーザーが必要としないアクセス許可は付与しないようにしてください。 たとえば、**セキュリティ ロール** セキュリティ操作の値を **[変更]** にすると、そのセキュリティ ロールに関連付けられていなくても、すべてのアクセス可能なセキュリティ ロールを編集できるアクセス許可が管理ユーザーに付与されます。  

8. セキュリティ操作の割り当ての構成が終了したら、 **[OK]** を選択して新しいセキュリティ ロールを保存します。  

##  <a name="configure-security-scopes-for-an-object"></a><a name="BKMK_ConfigSecScope"></a> オブジェクトのセキュリティ スコープの構成
 オブジェクトのセキュリティ スコープの関連付けは、セキュリティ スコープからではなくオブジェクトから管理します。 セキュリティ スコープがサポートしている直接的な構成は、セキュリティ スコープの名前と説明の変更のみです。 セキュリティ スコープのプロパティを表示するときに、セキュリティ スコープの名前と説明を変更するには、ユーザーに **セキュリティ スコープ** という保護可能なオブジェクトに対する **変更** のアクセス許可が指定されている必要があります。  

 Configuration Manager で新しいオブジェクトを作成すると、そのオブジェクトは、オブジェクトの作成に使用されたアカウントのセキュリティ ロールに関連付けられている各セキュリティ スコープと関連付けられます。 この動作は、これらのセキュリティ ロールが**作成**アクセス許可または**セキュリティ スコープの設定**アクセス許可を提供しているときに発生します。 作成した後で、オブジェクトのセキュリティ スコープを変更できます。  

 たとえば、新しい境界グループを作成するためのアクセス許可が付与されたセキュリティ ロールが割り当てられているとします。 新しい境界グループを作成するときに、特定のセキュリティ スコープを割り当てることはできません。 代わりに、割り当てられているセキュリティ ロールで使用できるセキュリティ スコープが、新しい境界グループに自動的に割り当てられます。 新しい境界グループを保存した後で、新しい境界グループに関連付けられているセキュリティ スコープを編集できます。  

 オブジェクトに関連付けられているセキュリティ スコープを構成するには、次の手順に従います。  

### <a name="to-configure-security-scopes-for-an-object"></a><a name="bkmk_config-sec-scope"></a> オブジェクトのセキュリティ スコープを構成するには  

1. Configuration Manager コンソールで、セキュリティ スコープへの割り当てをサポートするオブジェクトを選択します。  
2. **[ホーム]** タブの **[分類]** グループで、 **[セキュリティ スコープの設定]** を選択します。
3. **[セキュリティ スコープの設定]** ダイアログ ボックスで、このオブジェクトに関連付けられているセキュリティ スコープをオンまたはオフにします。 セキュリティ スコープをサポートする各オブジェクトが、少なくとも 1 つのセキュリティ スコープに割り当てられている必要があります。  
4. **[OK]** を選択して、割り当てられているキュリティ スコープを保存します。  

    > [!NOTE]  
    > 新しいオブジェクトを作成するときに、オブジェクトを複数のセキュリティ スコープに割り当てることができます。 オブジェクトに関連付けられているセキュリティ スコープの数を変更するには、オブジェクトの作成後に、この割り当てを変更する必要があります。

### <a name="to-configure-security-scopes-for-a-folder-starting-in-version-1906"></a><a name="bkmk_config-folder"></a> フォルダーのセキュリティ スコープを構成するには (バージョン 1906 以降)
<!--3600867-->

1. Configuration Manager コンソールで、フォルダーを選択します。  
1. リボンの **[フォルダー]** タブで、 **[セキュリティ スコープの設定]** を選択します。
   - フォルダーを右クリックし、 **[フォルダー]**  >  **[セキュリティ スコープの設定]** の順に選択することもできます。
1. **[セキュリティ スコープの設定]** ダイアログ ボックスで、フォルダーのセキュリティ スコープをオンまたはオフにします。 各フォルダーは、少なくとも 1 つのセキュリティ スコープに割り当てる必要があります。 すべてのフォルダーには、変更するまで**既定の**セキュリティ スコープが割り当てられます。
1. **[OK]** を選択して、割り当てられているキュリティ スコープを保存します。  

    > [!IMPORTANT]  
    > - 既存のセキュリティ ロールでは、Configuration Manager バージョン 1906 をインストールしたときに追加された**フォルダー クラス**のアクセス許可を自動的に取得します。 新しいセキュリティ ロールには**フォルダー クラス**のアクセス許可を追加し、既存のロールに環境に適したアクセス許可があることを確認する必要があります。
    > 
    > - ユーザーのセキュリティ スコープ外のフォルダーにあるアイテムは、そのユーザーがそのオブジェクトを作成した人物とセキュリティ スコープを共有していた場合、検索可能です。 <!--5602690-->

## <a name="configure-collections-to-manage-security"></a><a name="BKMK_ConfigColl"></a> セキュリティを管理するコレクションの構成

 ロール ベース管理にコレクションを構成する手順はありません。 コレクションには、ロール ベース管理構成はありません。 その代わりに、管理ユーザーを構成するときに、管理ユーザーにコレクションを割り当てます。 セキュリティ ロールが割り当てられたユーザーで有効になっているコレクション セキュリティ操作によって、コレクションとコレクション リソース (コレクション メンバー) に対する管理ユーザーのアクセス許可が決まります。  

 管理ユーザーがあるコレクションのアクセス許可を持っている場合、それらの管理ユーザーは、そのコレクションに限定されるコレクションのアクセス許可も持っています。 たとえば、組織で All Desktops という名前のコレクションが使用されているものとします。 また、All Desktops コレクションに限定されている All North America Desktops という名前のコレクションも存在します。 管理ユーザーが All Desktops のアクセス許可を持っている場合、その管理ユーザーはコレクション All North America Desktops に対しても同じアクセス許可を持っています。

 さらに、管理ユーザーは、コレクションに直接割り当てられている**削除**や**変更**のアクセス許可を使用することはできません。 ただし、コレクションに限定されているアクセス許可をコレクションで使用することができます。 前の例では、管理ユーザーはコレクション All North America Desktops を削除または変更できますが、コレクション All Desktops を削除または変更することはできません。  

## <a name="create-a-new-administrative-user"></a><a name="BKMK_Create_AdminUser"></a> 新しい管理ユーザーの作成

 個人またはセキュリティ グループのメンバーに Configuration Manager を管理するためのアクセス権を付与するには、Configuration Manager で管理ユーザーを作成し、ユーザーまたはユーザー グループの Windows アカウントを指定します。 Configuration Manager の各管理ユーザーに、少なくとも 1 つのセキュリティ ロールおよび少なくとも 1 つのセキュリティ スコープを割り当てる必要があります。 また、コレクションを割り当てて、管理ユーザーの管理スコープを制限することもできます。  

 新しい管理ユーザーを作成するには、次の手順に従います。  

### <a name="to-create-a-new-administrative-user"></a>新しい管理ユーザーを作成するには  

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[管理ユーザー]** を選択します。  
3. **[ホーム]** タブの **[作成]** グループで **[ユーザーまたはグループの追加]** を選択します。  
4. **[参照]** を選択し、この新しい管理ユーザーを使用するユーザー アカウントまたはグループを選択します。  

    > [!NOTE]  
    > コンソールベースの管理では、ドメイン ユーザーまたはセキュリティ グループのみ管理ユーザーとして指定できます。

5. **[関連付けられたセキュリティ ロール]** で、 **[追加]** を選択して使用可能なセキュリティ ロールの一覧を開き、1 つ以上のセキュリティ ロールのチェック ボックスをオンにしてから **[OK]** を選択します。  

6. 次の 2 つのオプションのいずれかを選択して、新しいユーザーに保護可能なオブジェクトの動作を定義します。  

    - **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** :このオプションは、 **[すべて]** セキュリティ スコープおよび **[すべてのシステム]** コレクションと **[すべてのユーザーおよびユーザー グループ]** コレクションを、管理ユーザーと関連付けます。 ユーザーに割り当てられているセキュリティ ロールによって、オブジェクトへのアクセスが定義されます。 この管理ユーザーが作成する新しいオブジェクトは、セキュリティ スコープ **[既定]** に割り当てられます。  

    - **[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ]** :このオプションでは、既定で管理ユーザーを、**既定**のセキュリティ スコープ、**すべてのシステム**、および**すべてのユーザーとユーザー グループ**の各コレクションに関連付けます。 ただし、実際のセキュリティ スコープとコレクションは、新しい管理ユーザーを作成するために使用したアカウントに関連付けられているセキュリティ グループとコレクションに限定されます。 このオプションは、管理ユーザーの管理スコープをカスタマイズするための、セキュリティ スコープとコレクションの追加と削除をサポートしています。  

    > [!IMPORTANT]  
    > 前述のオプションは、割り当てられている各セキュリティ スコープとコレクションを、管理ユーザーに割り当てられている各セキュリティ ロールに関連付けます。 3 つ目のオプション **[割り当てられたセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付ける]** を使用して、個々のセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付けることができます。 この 3 つ目のオプションは、新しい管理ユーザーを作成した後で、その管理ユーザーを変更するときに使用できます。  

7. 手順 6 で選択したオプションに応じて、次の操作を実行します。  

    - **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** を選択した場合は、 **[OK]** を選択してこの手順を完了します。  

    - **[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ]** を選択した場合は、 **[追加]** を選択して追加のコレクションとセキュリティ スコープを選択できます。 一覧で 1 つ以上のオブジェクトを選択し、 **[削除]** を選択して削除したりできます。 **[OK]** を選択してこの手順を完了します。  

## <a name="modify-the-administrative-scope-of-an-administrative-user"></a><a name="BKMK_ModAdminUser"></a> 管理ユーザーの管理スコープの変更

 管理ユーザーの管理スコープを変更するには、ユーザーに関連付けられているセキュリティ ロール、セキュリティ スコープ、およびコレクションを追加または削除します。 各管理ユーザーに、少なくとも 1 つのセキュリティ ロールおよび少なくとも 1 つのセキュリティ スコープを関連付ける必要があります。 1 つまたは複数のコレクションを、ユーザーの管理スコープに割り当てることが必要になる場合があります。 大部分のセキュリティ ロールはコレクションと対話し、コレクションが割り当てられていない場合は正しく機能しません。  

 管理ユーザーを変更するときに、割り当てられているセキュリティ ロールに保護可能なオブジェクトを関連付ける動作を変更できます。 次の 3 つの動作を選択できます。  

- **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** :このオプションは、 **[すべて]** スコープおよび **[すべてのシステム]** コレクションと **[すべてのユーザーおよびユーザー グループ]** コレクションを、管理ユーザーと関連付けます。 ユーザーに割り当てられているセキュリティ ロールによって、オブジェクトへのアクセスが定義されます。  

- **[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ]** :このオプションでは、管理ユーザーを構成するために使用したアカウントに関連付けられているのと同じセキュリティ スコープとコレクションに、管理ユーザーを関連付けます。 このオプションは、管理ユーザーの管理スコープをカスタマイズするための、セキュリティ ロールとコレクションの追加と削除をサポートしています。  

- **[割り当てられたセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付ける]** :このオプションでは、ユーザーに対して、個々のセキュリティ ロールと、特定のセキュリティ スコープおよびコレクション間の特定の関連付けを作成することができます。  

    > [!NOTE]  
    > このオプションは、管理ユーザーのプロパティを変更する場合のみ使用できます。  

保護可能なオブジェクトの動作の現在の構成によって、追加のセキュリティ ロールを割り当てるために使用する手順が変わります。 管理ユーザーを管理するときには、保護可能なオブジェクト用のさまざまなオプションに基づいた、次の手順に従います。  

管理ユーザーの保護可能なオブジェクトの構成を表示および管理するには、次の手順に従います。  

### <a name="to-view-and-manage-the-securable-object-behavior-for-an-administrative-user"></a>管理ユーザーの保護可能なオブジェクトの動作を表示および管理するには  

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[管理ユーザー]** を選択します。  
3. 変更する管理ユーザーを選択します。  
4. **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** を選択します。  
5. **[セキュリティ スコープ]** タブを選択し、この管理ユーザーの保護可能なオブジェクトの現在の構成を表示します。  
6. 保護可能なオブジェクトの動作を変更するには、保護可能なオブジェクトの動作に新しいオプションを選択します。 この構成を変更したら、次に必要な操作 (セキュリティ スコープとコレクション、この管理ユーザーのセキュリティ ロールの構成) を参照してください。  
7. **[OK]** を選び、手順を完了します。  

保護可能なオブジェクトの動作が **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** に設定されている管理ユーザーを変更するには、次の手順に従います。  

### <a name="for-option-all-instances-of-the-objects-that-are-related-to-the-assigned-security-roles"></a>オプション[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス] の場合  

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[管理ユーザー]** を選択します。  
3. 変更する管理ユーザーを選択します。  
4. **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** を選択します。  
5. **[セキュリティ スコープ]** タブを選択して、管理ユーザーが **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** に構成されていることを確認します。  
6. 割り当てられているセキュリティ ロールを変更するには、 **[セキュリティ ロール]** タブを選択します。  

    - この管理ユーザーに追加のセキュリティ ロールを割り当てるには、 **[追加]** を選択し、追加で割り当てる各セキュリティ ロールのチェック ボックスをオンにしてから、 **[OK]** を選択します。  
    - セキュリティ ロールを削除するには、一覧から 1 つまたは複数のセキュリティ ロールを選択し、 **[削除]** を選択します。

7. 保護可能なオブジェクトの動作を変更するには、 **[セキュリティ スコープ]** タブを選択し、保護可能なオブジェクトの動作に新しいオプションを選択します。 この構成を変更したら、次に必要な操作 (セキュリティ スコープとコレクション、この管理ユーザーのセキュリティ ロールの構成) を参照してください。  

    > [!NOTE]  
    > 保護可能なオブジェクトの動作が **[割り当てたセキュリティ ロールに関連付けられるオブジェクトのすべてのインスタンス]** に設定されている場合、特定のセキュリティ スコープおよびコレクションを追加または削除することはできません。  

8. **[OK]** を選択してこの手順を完了します。  

保護可能なオブジェクトの動作が **[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ]** に設定されている管理ユーザーを変更するには、次の手順に従います。  

### <a name="for-option-only-the-instances-of-objects-that-are-assigned-to-the-specified-security-scopes-and-collections"></a>オプション[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ] の場合  

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[管理ユーザー]** を選択します。  
3. 変更する管理ユーザーを選択します。  
4. **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** を選択します。  
5. **[セキュリティ スコープ]** タブを選択して、ユーザーが **[指定したセキュリティ スコープとコレクションに割り当てられるオブジェクトのインスタンスのみ]** に構成されていることを確認します。  
6. 割り当てられているセキュリティ ロールを変更するには、 **[セキュリティ ロール]** タブを選択します。  

    - このユーザーに追加のセキュリティ ロールを割り当てるには、 **[追加]** を選択し、追加で割り当てる各セキュリティ ロールのチェック ボックスをオンにしてから、 **[OK]** を選択します。  
    - セキュリティ ロールを削除するには、一覧から 1 つまたは複数のセキュリティ ロールを選択し、 **[削除]** を選択します。  
7. セキュリティ ロールに関連付けられているセキュリティ スコープとコレクションを変更するには、 **[セキュリティ スコープ]** タブを選択します。  

    - 新しいセキュリティ スコープまたはコレクションを、この管理ユーザーに割り当てられているセキュリティ ロールに関連付けるには、 **[追加]** を選択し、4 つのオプションのいずれかを選択します。 **[セキュリティ スコープ]** または **[コレクション]** を選択した場合、1 つ以上のオブジェクトのチェック ボックスをオンにしてから、 **[OK]** を選択します。  
    - セキュリティ スコープまたはコレクションを削除するには、オブジェクトを選択し、 **[削除]** を選択します。

8. **[OK]** を選択してこの手順を完了します。  

保護可能なオブジェクトの動作が **[割り当てられたセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付ける]** に設定されている管理ユーザーを変更するには、次の手順に従います。  

### <a name="for-option-associate-assigned-security-roles-with-specific-security-scopes-and-collections"></a>オプション[割り当てられたセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付ける] の場合  

1. Configuration Manager コンソールで、 **[管理]** を選択します。  
2. **[管理]** ワークスペースで、 **[セキュリティ]** を展開してから、 **[管理ユーザー]** を選択します。  
3. 変更する管理ユーザーを選択します。  
4. **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** を選択します。  
5. **[セキュリティ スコープ]** タブを選択して、管理ユーザーが **[割り当てられたセキュリティ ロールを特定のセキュリティ スコープとコレクションに関連付ける]** に構成されていることを確認します。  
6. 割り当てられているセキュリティ ロールを変更するには、 **[セキュリティ ロール]** タブを選択します。  

    - この管理ユーザーに追加のセキュリティ ロールを割り当てるには、 **[追加]** を選択します。 **[セキュリティ ロールの追加]** ダイアログ ボックスで、1 つ以上の使用可能なセキュリティ ロールを選択してから、 **[追加]** を選択してから、選択したセキュリティ ロールに関連付けるオブジェクトの種類を選択します。 **[セキュリティ スコープ]** または **[コレクション]** を選択した場合、1 つ以上のオブジェクトのチェック ボックスをオンにしてから、 **[OK]** を選択します。  

        > [!NOTE]  
        > 選択したセキュリティ ロールを管理ユーザーに割り当てる前に、少なくとも 1 つのセキュリティ スコープを構成する必要があります。 複数のセキュリティ ルールを選択した場合、構成する各セキュリティ スコープとコレクションが、選択した各セキュリティ ロールに関連付けられます。  

    - セキュリティ ロールを削除するには、一覧から 1 つまたは複数のセキュリティ ロールを選択し、 **[削除]** を選択します。  

7. 特定のセキュリティ ロールに関連付けられたセキュリティ スコープとコレクションを変更するには、 **[セキュリティ スコープ]** タブを選択し、セキュリティ ロールを選択してから、 **[編集]** を選択します。  

    - 新しいオブジェクトをこのセキュリティ ロールに関連付けるには、 **[追加]** を選択し、選択したセキュリティ ロールに関連付けるオブジェクトの種類を選択します。 **[セキュリティ スコープ]** または **[コレクション]** を選択した場合、1 つ以上のオブジェクトのチェック ボックスをオンにしてから、 **[OK]** を選択します。  

        > [!NOTE]  
        > 少なくとも 1 つのセキュリティ スコープを構成する必要があります。  

    - このセキュリティ ロールに関連付けられているセキュリティ スコープまたはコレクションを削除するには、オブジェクトを選択し、 **[削除]** を選択します。  

    - 関連付けられたオブジェクトの変更が終了したら、 **[OK]** を選択します。  

8. **[OK]** を選択してこの手順を完了します。  

    > [!CAUTION]  
    > セキュリティ ロールによって管理ユーザーにコレクション展開のアクセス許可が付与されると、これらの管理ユーザーは、該当するセキュリティ スコープが異なるセキュリティ ロールに関連付けられている場合でも、オブジェクトの **[読み取り]** アクセス許可を持っている任意のセキュリティ スコープからオブジェクトを配布できるようになります。  

## <a name="next-steps"></a>次のステップ

[Configuration Manager で使用されるアカウント](../../../plan-design/hierarchy/accounts.md)