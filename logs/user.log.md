```bash
➜  ~ kubectl logs --tail=200 user-svc-97ccff8bd-5bpsb
Executing (default): CREATE TABLE IF NOT EXISTS "User" ("email" VARCHAR(255) , "passwordHash" VARCHAR(255), "createdAt" TIMESTAMP WITH TIME ZONE, "updatedAt" TIMESTAMP WITH TIME ZONE, PRIMARY KEY ("email"));
Executing (default): SELECT i.relname AS name, ix.indisprimary AS primary, ix.indisunique AS unique, ix.indkey AS indkey, array_agg(a.attnum) as column_indexes, array_agg(a.attname) AS column_names, pg_get_indexdef(ix.indexrelid) AS definition FROM pg_class t, pg_class i, pg_index ix, pg_attribute a WHERE t.oid = ix.indrelid AND i.oid = ix.indexrelid AND a.attrelid = t.oid AND t.relkind = 'r' and t.relname = 'User' GROUP BY i.relname, ix.indexrelid, ix.indisprimary, ix.indisunique, ix.indkey ORDER BY i.relname;
server running port 9898
press CTRL+C to stop server
11/2/2020, 2:30:57 PM - 0c6b1880-3adf-4b80-bd2f-2f8f03d20b5a: Login action started
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'pacho@fake.com';
11/2/2020, 2:30:57 PM - 0c6b1880-3adf-4b80-bd2f-2f8f03d20b5a: Login action finished with error: Unauthorized - User not found
11/2/2020, 2:31:14 PM - 2c8c25fc-e6b6-4a0c-877d-8b5a168332ac: Login action started
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'mochi@fake.com';
11/2/2020, 2:31:14 PM - 2c8c25fc-e6b6-4a0c-877d-8b5a168332ac: Login action finished Ok for mochi@fake.com
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'francisco@fake.com';
Executing (default): INSERT INTO "User" ("email","passwordHash","createdAt","updatedAt") VALUES ($1,$2,$3,$4) RETURNING *;
```

```bash
➜  ~ kubectl logs --tail=200 user-svc-97ccff8bd-pml7h
Executing (default): CREATE TABLE IF NOT EXISTS "User" ("email" VARCHAR(255) , "passwordHash" VARCHAR(255), "createdAt" TIMESTAMP WITH TIME ZONE, "updatedAt" TIMESTAMP WITH TIME ZONE, PRIMARY KEY ("email"));
Executing (default): SELECT i.relname AS name, ix.indisprimary AS primary, ix.indisunique AS unique, ix.indkey AS indkey, array_agg(a.attnum) as column_indexes, array_agg(a.attname) AS column_names, pg_get_indexdef(ix.indexrelid) AS definition FROM pg_class t, pg_class i, pg_index ix, pg_attribute a WHERE t.oid = ix.indrelid AND i.oid = ix.indexrelid AND a.attrelid = t.oid AND t.relkind = 'r' and t.relname = 'User' GROUP BY i.relname, ix.indexrelid, ix.indisprimary, ix.indisunique, ix.indkey ORDER BY i.relname;
server running port 9898
press CTRL+C to stop server
11/2/2020, 1:14:06 PM - 11aa95bf-55bc-47ee-aaa6-439adb6f4d01: Login action started
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'mochi@fake.com';
11/2/2020, 1:14:06 PM - 11aa95bf-55bc-47ee-aaa6-439adb6f4d01: Login action finished Ok for mochi@fake.com
11/2/2020, 1:14:24 PM - f1fc5353-3c30-464d-bbff-d2b0334cbd81: Login action started
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'asd@opmp.com';
11/2/2020, 1:14:24 PM - f1fc5353-3c30-464d-bbff-d2b0334cbd81: Login action finished with error: Unauthorized - User not found
11/2/2020, 1:42:17 PM - 66e3cf94-9068-4c36-8cb7-68cde43242fb: Login action started
Executing (default): SELECT "email", "passwordHash", "createdAt", "updatedAt" FROM "User" AS "User" WHERE "User"."email" = 'mochi@fake.com';
11/2/2020, 1:42:17 PM - 66e3cf94-9068-4c36-8cb7-68cde43242fb: Login action finished Ok for mochi@fake.com
```